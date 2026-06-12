---
title: "How to know whether UDP/IP or TCP/IP is being used in a LAN"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by g_ramesh on 2012-03-28
Hi,
is it possible to know whether UDP/IP or TCP/IP is being used in a LAN?
If so how to check/verify ? Please tell me.

---

### Post by spynappels on 2012-03-28
In an average LAN, both will be used. What specifically do you want to find out?

---

### Post by g_ramesh on 2012-03-28
> **spynappels said:**
> In an average LAN, both will be used. What specifically do you want to find out?

Thanks spynappels for your reply. 

A candidate in an exam was asked to tell which protocol is used in that particular network.

The network is based on RHEL 3 and RHEL 4. I don't want to install any third party tools. 
Please tell me is it possible to know this, using the tools inbuilt into RHEL 3&4.

---

### Post by spynappels on 2012-03-28
Forums policy do not allow homework or assignment questions to be posted, is this for your own exam?

In general terms, you could look at taking a network capture, this would show which protocols are present on the wire.

Other than this, I'm not comfortable answering exam questions.

---

### Post by g_ramesh on 2012-03-29
> **spynappels said:**
> Forums policy do not allow homework or assignment questions to be posted, is this for your own exam?

In general terms, you could look at taking a network capture, this would show which protocols are present on the wire.

Other than this, I'm not comfortable answering exam questions.

Thanks for your reply. this is for my own knowledge. Please tell me the tools to be used which are inbuilt.

---

### Post by spynappels on 2012-03-29
Have a look at tcpdump or tshark for CLI use, Wireshark for GUI use.

---

### Post by haqking on 2012-03-29
> **g_ramesh said:**
> Thanks spynappels for your reply. 

A candidate in an exam was asked to tell which protocol is used in that particular network.

The network is based on RHEL 3 and RHEL 4. I don't want to install any third party tools. 
Please tell me is it possible to know this, using the tools inbuilt into RHEL 3&4.

A network itself wont use UDP over TCP it will be the service which decides.

using RHEL wont dictate UDP over TCP but the services that are running will regardless of the OS.

As said a typical LAN would be using both at for different purposes

The difference between the 2 is the service.

The LAN would be using TCP/IP suite of protocols, TCP is connection oriented and UDP is connectionless.

For example if you have DNS then UDP is being used as it is largely a connectionless service, or TFTP would use UDP.

Any service which doesnt need to establish a connection for communication may use UDP as no 3 way handshake takes place, such as DNS, DHCP, SNMP etc etc

You can use any packet sniffer such as wireshark to capture the packets and see what service is using a given protocol.

TCP/IP  is a suite which consists of many protocols UDP and TCP being 2 of them and they all are used for different purposes by different services and operate at different layers.

Cheers

---

### Post by g_ramesh on 2012-03-29
> **haqking said:**
> A network itself wont use UDP over TCP it will be the service which decides.

using RHEL wont dictate UDP over TCP but the services that are running will regardless of the OS.

As said a typical LAN would be using both at for different purposes

The difference between the 2 is the service.

The LAN would be using TCP/IP suite of protocols, TCP is connection oriented and UDP is connectionless.

For example if you have DNS then UDP is being used as it is largely a connectionless service, or TFTP would use UDP.

Any service which doesnt need to establish a connection for communication may use UDP as no 3 way handshake takes place, such as DNS, DHCP, SNMP etc etc

You can use any packet sniffer such as wireshark to capture the packets and see what service is using a given protocol.

TCP/IP  is a suite which consists of many protocols UDP and TCP being 2 of them and they all are used for different purposes by different services and operate at different layers.

Cheers
Thanks a lot for your time. I am not allowed to install any other program I have to use inbuilt programs.



> spynappels 	 		 		Have a look at tcpdump or tshark for CLI use, Wireshark for GUI use. 	


Thanks will try tcpdump or tshark as no GUI is used.

---

### Post by haqking on 2012-03-29
> **g_ramesh said:**
> Thanks a lot for your time. I am not allowed to install any other program I have to use inbuilt programs.



Well like i said, you dont really need a packet sniffer to see what protocol is being used.

IF you have DHCP or DNS for example then UDP is being used as well as TCP, they will both be used amongst many other protocols.

A LAN doesnt use one or the other, if the LAN operates on TCP/IP which most do these days then TCP and UDP will be used at different times depending on the services in use and one is connectionless and one is connection oriented as stated.

Cheers

---

### Post by CharlesA on 2012-03-29
> **haqking said:**
> Well like i said, you dont really need a packet sniffer to see what protocol is being used.

IF you have DHCP or DNS for example then UDP is being used as well as TCP, they will both be used amongst many other protocols.

A LAN doesnt use one or the other, if the LAN operates on TCP/IP which most do these days then TCP and UDP will be used at different times depending on the services in use and one is connectionless and one is connection oriented as stated.

Cheers
What he said ^.

I believe most services use TCP but some such as DNS or DHCP use UDP.

Part of it is also the whole connection-oriented vs connection-less thing and also the error checking bit that TCP does and UDP doesn't do.

---

### Post by g_ramesh on 2012-04-04
Thanks all for your replies.  As said by many of you the TCP and UDP are both used in a LAN, I was told that in our LAN using RHEL3 the particular application software is using UDP to exchange messages and the other application using TCP.
For this reason I wanted to know which one i.e TCp or UDP is used.

---

### Post by haqking on 2012-04-04
> **g_ramesh said:**
> Thanks all for your replies.  As said by many of you the TCP and UDP are both used in a LAN, I was told that in our LAN using RHEL3 the particular application software is using UDP to exchange messages and the other application using TCP.
For this reason I wanted to know which one i.e TCp or UDP is used.

Well what is the application ?

---

### Post by g_ramesh on 2012-04-04
> **haqking said:**
> Well what is the application ?

thanks for your reply, the application is related to aviation. It receives inputs from various sources and processes to the requirement of the user.

---

### Post by mikejonesey on 2012-04-04
sharky and george, the greatest crime busters of the sea...

wire shark is a cool tool...

ps on the server (the host running application) you can run the following to check what each tcp port is doing;

netstat -tln | tail -n +3 | awk '{print $4}' | sed 's/.*://' | sort -u | while read ap; do lsof -i :$ap; done

---

