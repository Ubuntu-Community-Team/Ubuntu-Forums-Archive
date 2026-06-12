---
title: "knetworkmanager 802.1x wired authentication"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by DMA02 on 2010-05-28
Hi guys,

I have installed (right from the CD) Kubuntu 10.04 and it seems to be running great.

I have it running in a company where all machines are Windows XP (SP2) who connect to the network via a static IPs and 802.1x authentication with certificate.

I gathered as much info as possible from my windows PC, and I exported 2 certificates (they were listed in the "Smart Card or Certificate Properties" window as Base64 format.)

When I configure the network settings using KNetworkManager that comes with kubuntu I am not having a lot of success connecting to the network.

I set all the manual IP settings. The 802.1x authentication I try to set it as follows

CA Certificate: points to the base64 encoded certificate file
Use System CA certificate is unchecked
PEAP version: Automatic
Inner Authentication: MSCHAPv2
User: my windows login user name (I tried with and without domain ie, DOMAIN\user)
Password: my windows login password

Nothing seems to happen. I look in /var/log/message and I see the eth0 link going up and then down continuously. I don't know if the authentication is failing or if there is some other problem.

I read somewhere that I might need likewise-open installed first to connect to the domain ? 

On top of all that, is there a proper windows -> ubuntu migration of netwrok settings concerning 802.1x and which fields relate to what?

Any help, suggestions, links are most appreciated. I am sure a lot of people who install ubuntu on company networks would find this useful.

---

