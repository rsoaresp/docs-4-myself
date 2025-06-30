# A quick introduction to networks for beginners[^1]
By Rafael Soares Pinto 

[^1]:  This is an amalgamation of different resources that tries to give an introduction on how computer networks are implemented. Its content 
comes from a lot of different resources, from wikipedia to blog posts crawled from google searches.



A computer network is a collection of communicating computers and other devices, such as printers and smartphones. Today almost 
all computers are connected to a computer network, such as the global Internet or an embedded network such as those found in modern cars.

A network address is an identifier for a node or host on a telecommunications network. Network addresses are designed to be unique 
identifiers across the network, although some networks allow for local, private addresses, or locally administered addresses that 
may not be unique. 

The most common network addressing architecture is Internet Protocol version 4 (IPv4), but its successor, IPv6, has been increasingly 
deployed since approximately 2006. 

An IPv4 address is a numerical label consisting of 32 bits arranged into blocks in the format (8 bits).(8 bits).(8 bits).(8 bits). IP addresses are often written and 
displayed in human-readable notations, such as 172.16.254.1

> 172 (10101100) . 16 (00010000) . 254 (11111110) . 1 (00000001)

What is the number of addresses available on IPv4? We have $`(2^8) \times (2^8) \times (2^8) \times (2^8) = 2^{32}`$ ~ 4.3 billion addresses[^2]

[^2]:  This seems like a big number but we exhausted the addresses available on IPv4 quite fast, which was the cause of the IPV6 implementation.


## Subnetworks

$`2^{32}`$ addresses is a large ammount and most of the time we need the concept of a subnetwork (or subnet), which is a logical subdivision of an IP network. The practice of 
dividing a network into two or more networks is called subnetting. 

Computers that belong to the same subnet are addressed with an identical group of its most-significant bits of their IP addresses. This results in the logical division of an IP address into two fields: 

  - The network address is a series of numerical digits pointing to the subnetwork's unique identifier 
  - The host address is a series of numbers indicating the host or individual device identifier on the network

The classful network is an obsolete subnetting addressing architecture used in the Internet from 1981 until the introduction of Classless Inter-Domain Routing (CIDR) in 1993

### Class A
A Class A IPv4 address has 8 network prefix bits. For example, consider 44.0.0.1, where 44 is the network address and 0.0.1 is the host address.

### Class B
A Class B IPv4 address has 16 network prefix bits. For example, consider 128.16.0.2, where 128.16 is the network address and 0.2 is the host address.

### Class C
A Class C IPv4 address has 24 network prefix bits. For instance, consider 192.168.1.100, where 192.168.1 is the network address and 100 is the host address. 

In a classful addressing system, each class supported a fixed number of devices:
 - Class A supported 224 = 16,777,214 hosts
 - Class B supported 216 = 65,534 hosts
 - Class C supported 28 = 254 hosts


An organization with 300 devices couldn’t have used a Class C IP address, which only permitted 254 devices. So, the organization would’ve been forced to apply for a Class B IP address, 
which provided 65,534 unique host addresses. However, only 300 devices would’ve been connected, which would’ve left 65,234 unused IP address spaces.

## CIDR

Classless Inter-Domain Routing (CIDR /ˈsaɪdər, ˈsɪ-/) is a method for allocating IP addresses for IP routing. The Internet Engineering Task Force introduced CIDR in 1993 to replace 
the previous classful network addressing architecture on the Internet. Its goal was to slow the growth of routing tables on routers across the Internet, and to help slow the rapid 
exhaustion of IPv4 addresses. In the CIDR method, IP addresses are described as consisting of two groups of bits in the address: the most significant bits are the network prefix, 
which identifies a whole network or subnet, and the least significant set forms the host identifier, which specifies a particular interface of a host on that network

![](https://miro.medium.com/v2/resize:fit:1400/1*-Z-VPtPRYTCPg-g_T5M8lA.png)


#### Examples of CIDR blocks

10.0.1.0/24 = 00001010.00000000.00000001.**00000000** → 10.0.1.0 Até 10.0.1.255

10.0.1.0/23 = 00001010.00000000.0000000**1.00000000** → 10.0.0.0 Até 10.0.1.255

10.0.1.0/22 = 00001010.00000000.000000**01.00000000** → 10.0.0.0 Até 10.0.3.255


## Private subnets

Three non-overlapping ranges of IPv4 addresses for private networks are reserved. These addresses are not routed on the Internet and thus their use need not be coordinated with an 
IP address registry. Any user may use any of the reserved blocks.

| Name | CIDR block | Address range | Numbers addresses available | Classful description |
| --- | --- | --- |  --- | --- |
| 24-bit block | 10.0.0.0/8 | 10.0.0.0 – 10.255.255.255 |16777216 | Single Class A |
| 20-bit block | 172.16.0.0/12 | 172.16.0.0 – 172.31.255.255 | 1048576 | Contiguous range of 16 Class B blocks |
| 16-bit block | 192.168.0.0/16 | 192.168.0.0 – 192.168.255.255 | 65536 |Contiguous range of 256 Class C blocks |


## Network address translation

Network Address Translation (*NAT*) is a method used to map private IP addresses within a local subnetwork to a public IP address for communication over the internet. It conserves IPv4 
addresses by allowing multiple devices to share a single public IP. NAT operates at the router level, modifying information in the IP header of packets while they are 
in transit across a traffic routing device. NAT enhances security by hiding internal network structures but 

![network address translation](https://github.com/user-attachments/assets/da026ace-62e1-488f-aba8-bdcece1a72a3)




