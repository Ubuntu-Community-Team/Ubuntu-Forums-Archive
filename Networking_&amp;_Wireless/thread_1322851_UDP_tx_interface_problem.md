---
title: "UDP tx interface problem"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by MGLMGL on 2009-11-11
Hello,

I am new to Ubuntu and have installed version 9.04.

I am trying to transmit UDP data from one computer to another. The transmitting computer has three interface cards. I can transmit data from the main interface (eth0) but not eth1, which is the one I would like to use. I have set the interfaces file up as follows: -

 auto eth0
iface eth0 inet static
   hwaddress ether 00:10:18:2b:4a:83
   address 192.168.108.201
   netmask 255.255.255.0
   network 192.168.108.0
   broadcast 192.168.108.255
   gateway 192.168.108.1
   metric 1

auto eth1
iface eth1 inet static
   hwaddress ether 00:18:f3:f9:3e:0e
   address 10.10.27.1
   netmask 255.255.255.0
   network 10.10.27.0
   broadcast 10.10.27.255
   gateway 10.10.27.1
   metric 1000

auto eth2
iface eth2 inet static
   hwaddress ether 00:18:f3:f9:3e:e7
   address 10.10.28.1
   netmask 255.255.255.0
   network 10.10.28.0
   broadcast 10.10.28.255
   gateway 10.10.28.1
   metric 1000

auto lo
iface lo inet loopback



And the code I am using to set up the socket is: -

int create_udp_socket(int port) 
{
       int    s;
  struct sockaddr_in host_address;
	
  s=socket(PF_INET, SOCK_DGRAM, IPPROTO_UDP);
  if (s < 0) 
  {
    perror("socket()");
    return -1;
  }
	
  memset((void*)&host_address, 0, sizeof(host_address));
  host_address.sin_family=AF_INET;
  host_address.sin_addr.s_addr=inet_addr("10.10.27.1");                            /*Interface IP being used*/
  host_address.sin_port=htons(port);
	
  if (bind(s, (struct sockaddr*)&host_address, sizeof(host_address)) < 0) 
  {
    perror("bind() ERROR");
    return -1;
  }
	return s;
}


Can anyone see where I'm going wrong?

Thanks in advance!
Matt

---

