---
title: "chillispot setting ip statically"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by slaz on 2009-10-20
Hello,
 
I have a machine running slackware 11.0, dansguardian, squid, and chillispot. I want to have dansguardian have different filter groups. But I am not sure if i can do this since chillispot is using dhcp to hand out ip addresses to clients. I have dansguardian set to default, meaning it only has one filter group, and listens to the ip address chillispot is handing out. What I was thinking of doing is setting the wireless network card, with a static ip address. But do I have to go into the chilli.conf file and change to use a static ip range. I have tried to set a static ip address using the same ip range chillispot hands out. But I don't redirected to the login page. Is this because chilli.conf is only using dhcp for ip addresses. Is this even possible to do what I am asking. The reason behind this is I want to filter by ip address, with squid running as a transparent proxy so some users don't have to make changes to there browsers. But I want to have some other computers with wirelesscards to get the same ip address handed out to them. 
Thanks for any help,
Lost

---

