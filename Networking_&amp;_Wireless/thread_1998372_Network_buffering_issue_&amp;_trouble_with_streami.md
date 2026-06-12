---
title: "Network buffering issue &amp; trouble with streaming"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by xigen on 2012-06-06
Hello,

I got a new TV (weee!)
I would like to stream stuff to the TV 
I get buffering issues and network delays

Below is the output from a network traffic analysis tool with the buffer highlighted in[COLOR="Red"] Red.[/COLOR] 

Network:  
-- Ubuntu 11.04
-- Cisco/Linksys SE2800 gigabit switch
-- Belkin N router.  Connected via cat5  wire to switch & PC. 

My questions:
1) is this a local issue?
2) Is it a bandwidth issue?
3)  Is it my ISP?
4) or ... other ....

As always -- thank you.

The ICSI Netalyzr
Start » Analysis » Results
Result Summary
+ – (help)
199-83-220-173.PUBLIC.monkeybrains.net / 199.83.220.173
Recorded at 15:58 EDT (19:58 UTC), Jun 05 2012. Permalink. Client/server transcript.
Summary of Noteworthy Events + –
Minor Aberrations –

    Fragmented UDP traffic is blocked
    The network measured bursts of packet loss
    Network packet buffering may be excessive
    The network blocks some or all EDNS replies
    Your DNS server accepts unusual glue records
    Your web browser has a problem accessing IPv6 sites
    Your computer's clock is slightly slow 

Address-based Tests + –
NAT detection (?): NAT Detected +
Local Network Interfaces (?): OK +
DNS-based host information (?): OK +
NAT support for Universal Plug and Play (UPnP) (?): Yes +
Reachability Tests + –
TCP connectivity (?): OK +
UDP connectivity (?): Note –
Basic UDP access is available.

The applet was able to send fragmented UDP traffic.

The applet was unable to receive fragmented UDP traffic. The most likely cause is an error in your network's firewall configuration or NAT.
The maximum packet successfully received was 1472 bytes of payload.
Direct UDP access to remote DNS servers (port 53) is allowed.
Direct UDP access to remote NTP servers (port 123) is allowed.
Direct UDP access to remote NetBIOS NS servers (port 137) is blocked.
Direct UDP access to remote NetBIOS DGM servers (port 138) is allowed.
Direct UDP access to remote IKE key exchange servers (port 500) is allowed.
Direct UDP access to remote OpenVPN servers (port 1194) is allowed.
Direct UDP access to remote Slammer servers (port 1434) is allowed.
Direct UDP access to remote L2 tunneling servers (port 1701) is allowed.
Direct UDP access to remote IPSec NAT servers (port 4500) is allowed.
Direct UDP access to remote RTP servers (port 5004) is allowed.
Direct UDP access to remote RTCP servers (port 5005) is allowed.
Direct UDP access to remote SIP servers (port 5060) is allowed.
Direct UDP access to remote VoIP servers (port 7078) is allowed.
Direct UDP access to remote VoIP servers (port 7082) is allowed.
Direct UDP access to remote SCTP servers (port 9899) is allowed.
Direct UDP access to remote Steam gaming servers (port 27005) is allowed.
Direct UDP access to remote Steam gaming servers (port 27015) is allowed.
Traceroute (?): OK +
Path MTU (?): OK +
Network Access Link Properties + –
Network latency measurements (?): Latency: 110ms Loss: 0.0% –
The round-trip time (RTT) between your computer and our server is 110 msec, which is good.
We recorded no packet loss between your system and our server.
During this test, the applet observed one reordered packet.
TCP connection setup latency (?): 100ms –
The time it takes your computer to set up a TCP connection with our server is 100 msec, which is good.
Network background health measurement (?): 1 transient outages, longest: 7.4 seconds –
During most of Netalyzr's execution, the applet continuously measures the state of the network in the background, looking for short outages. During testing, the applet observed 1 such outages. The longest outage lasted for 7.4 seconds. This suggests a general problem with the network where connectivity is intermittent. This loss might also cause some of Netalyzr's other tests to produce incorrect results.
Network bandwidth (?): Upload 8.1 Mbit/sec, Download 4.1 Mbit/sec –
Your Uplink: We measured your uplink's sending bandwidth at 8.1 Mbit/sec. This level of bandwidth works well for many users.
During this test, the applet observed one reordered packet.
Your Downlink: We measured your downlink's receiving bandwidth at 4.1 Mbit/sec. This level of bandwidth works well for many users.
During this test, the applet observed 59 reordered packets.
[COLOR="Red"]Network buffer measurements (?): Uplink 969 ms, Downlink 1300 ms –
We estimate your uplink as having 970 msec of buffering. This is quite high, and you may experience substantial disruption to your network performance when performing interactive tasks such as web-surfing while simultaneously conducting large uploads. With such a buffer, real-time applications such as games or audio chat can work quite poorly when conducting large uploads at the same time.
We estimate your downlink as having 1300 msec of buffering. This is quite high, and you may experience substantial disruption to your network performance when performing interactive tasks such as web-surfing while simultaneously conducting large downloads. With such a buffer, real-time applications such as games or audio chat can work quite poorly when conducting large downloads at the same time.[/COLOR]
HTTP Tests + –
Address-based HTTP proxy detection (?): OK +
Content-based HTTP proxy detection (?): OK +
HTTP proxy detection via malformed requests (?): OK +
Filetype-based filtering (?): OK +
HTTP caching behavior (?): OK +
JavaScript-based tests (?): OK +
DNS Tests + –
Restricted domain DNS lookup (?): OK +
Unrestricted domain DNS lookup (?): OK +
Direct DNS support (?): OK +
Direct EDNS support (?): Note –
EDNS-enabled requests for small responses are answered successfully.
EDNS-enabled requests for medium-sized responses are answered successfully.
EDNS-enabled requests for large responses remain unanswered. This suggests that a proxy or firewall is unable to handle large extended DNS requests or fragmented UDP traffic.
DNS resolver address (?): OK +
DNS resolver properties (?): Lookup latency 140ms +
Direct probing of DNS resolvers (?): +
DNS glue policy (?): Warning –
Your ISP's DNS resolver does not accept generic additional (glue) records — good.
Your ISP's DNS resolver does not accept additional (glue) records which correspond to nameservers.
Your ISP's DNS resolver follows CNAMEs regardless of their location. This is very unusual.
DNS resolver port randomization (?): OK +
DNS lookups of popular domains (?): OK +
DNS external proxy (?): OK +
DNS results wildcarding (?): OK +
DNS-level redirection of specific sites (?): OK +
Direct probing of DNS roots (?): +
IPv6 Tests + –
DNS support for IPv6 (?): OK +
IPv4, IPv6, and your web browser (?): IPv6 connectivity problem –
Your browser successfully fetched a test image from our IPv6 server. Unfortunately, this is substantially slower than IPv4: it took 0.5 seconds longer to fetch the image over IPv6 compared to IPv4. Your browser prefers IPv4 over IPv6.
IPv6 connectivity (?): OK +
IPv6 TCP connectivity (?): OK +
IPv6 Path MTU (?): OK +
IPv6 Traceroute (?): OK +
Host Properties + –
System clock accuracy (?): Warning –
Your computer's clock is 12 seconds slow.
Browser properties (?): OK +
Uploaded data (?): OK +
Feedback + –
User-provided feedback

---

