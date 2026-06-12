---
title: "Unknown large uploads."
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by CaptainofCrunch on 2012-02-23
I have noticed a couple of times that my network has been uploading and downloading at about 200-300Kbs when I am in the homescreen with no updates, browsers or any other programs running thats would cause such high network traffic. When I seen this happen I immediately switched off the internet for a few minutes and when I turned it back on network usage was back to normal.

I tried looking around the internet and on here for a solution but I obviously haven't found an answer yet.

Anybody got an answer for this?

---

### Post by winh8r on 2012-02-23
Could be your email program checking for new mail/updating local mailbox, or maybe the update manager checking status in the background if it is set to do this.

Also , a lot of google services tend to "take control" of when they do things. 

Is it happening regularly or just a spontaneous thing, by that I mean is it just after login or does it happen randomly after login?

---

### Post by Palmstroem on 2012-02-23
I would nevertheless suspect updates going on in the background. Anyway, you can easily monitor your net traffic with tools like tcpdump or wireshark. Cheers!

---

### Post by CaptainofCrunch on 2012-02-23
> **winh8r said:**
> Could be your email program checking for new mail/updating local mailbox, or maybe the update manager checking status in the background if it is set to do this.

Also , a lot of google services tend to "take control" of when they do things. 

Is it happening regularly or just a spontaneous thing, by that I mean is it just after login or does it happen randomly after login?

I don't have any email client running on my computer.

And I'm pretty sure there aren't any google services running. (What do you mean by google services??)

In the past 3 months its happened about 5 time and not at any specific time. i.e. after login.

---

### Post by CaptainofCrunch on 2012-02-23
> **Palmstroem said:**
> I would nevertheless suspect updates going on in the background. Anyway, you can easily monitor your net traffic with tools like tcpdump or wireshark. Cheers!

Next time it happens I''l switch on wireshark and see what it tells me. But to be honest I don't understand most of the stuff that comes up on that. I'm still learning.

---

### Post by lisati on 2012-02-23
Update manager? My laptop checks for updates regularly, and this sometimes creates a (usually) short lived burst of activity.

---

### Post by winh8r on 2012-02-23
> **CaptainofCrunch said:**
> I don't have any email client running on my computer.

And I'm pretty sure there aren't any google services running. (What do you mean by google services??)

In the past 3 months its happened about 5 time and not at any specific time. i.e. after login.

Well, going by what you have said , I would say the best thing to do is , when it happens again, check the system monitor/processes or open a terminal and enter the 

```
top
```
command and see what is running.

My reference to google services was a bit of a broad spectrum thing but basically if you have any of the things listed here:
[https://en.wikipedia.org/wiki/List_of_Google_products]("https://en.wikipedia.org/wiki/List_of_Google_products")
installed or use them regularly then they could be updating/communicating in the background.

Are you running a firewall?

---

### Post by CaptainofCrunch on 2012-02-23
> **lisati said:**
> Update manager? My laptop checks for updates regularly, and this sometimes creates a (usually) short lived burst of activity.

The times I've seen it happening it lasted for about 20 seconds at around 300Kbs. But as soon as I see it I switch off my internet at the mains.

Would the update manager be downloading and these speeds and not uploading??

---

### Post by CaptainofCrunch on 2012-02-23
> **winh8r said:**
> Well, going by what you have said , I would say the best thing to do is , when it happens again, check the system monitor/processes or open a terminal and enter the 

```
top
```
command and see what is running.

My reference to google services was a bit of a broad spectrum thing but basically if you have any of the things listed here:
[https://en.wikipedia.org/wiki/List_of_Google_products]("https://en.wikipedia.org/wiki/List_of_Google_products")
installed or use them regularly then they could be updating/communicating in the background.

Are you running a firewall?

I will check system monitor/processes next time I see it happening.

The only google program I have on my system is Google Earth and I haven't used that since I installed it because its been acting like a little bitch, the globe doesn't show up at all and most of the menus are greyed out.

Firewall, yes. Just the default.

---

### Post by winh8r on 2012-02-23
Update manager will check what packages are installed and what has been used /installed since update manager last ran , then it will check with repository for available updates and any that are available or required will either be notified to you, downloaded in the background , or automatically installed. Depending on how you have your update manager set to run and behave.

It is usually a fairly quick process,depending on what is needed, some updates are only a few Kb's whilst others can run to many Mb's .

If nothing else is running then it will use full speed available on the connection.

---

### Post by CaptainofCrunch on 2012-02-23
> **winh8r said:**
> Update manager will check what packages are installed and what has been used /installed since update manager last ran , then it will check with repository for available updates and any that are available or required will either be notified to you, downloaded in the background , or automatically installed. Depending on how you have your update manager set to run and behave.

It is usually a fairly quick process,depending on what is needed, some updates are only a few Kb's whilst others can run to many Mb's .

If nothing else is running then it will use full speed available on the connection.


I have Update Manager to check daily for updates.

I did a check for updates there to see the network usage of it and it never went past about 4-5Kbs, upload and download speed. There was nothing to update. I'll check it again but it just seems a little strange that the update manager would use such high upload speeds for me anyway, when I run a speed test of my broadband I get a max of 0.4Mbs so 400Kbs, which means that whatever is doing this is using basically all my upload bandwidth.

I understand what you are saying and I'm in no way an expert with Ubuntu, I'm still trying to understand most of it.

---

### Post by matt_symes on 2012-02-23
Hi

When i need to see what is using my bandwidth, i use nethogs.

```
sudo apt-get install nethogs
```

It will give you a second by second account of what is using your bandwidth at that moment. Very easy to use and to see what is happening. Read the man page for it.

I have found it useful for identifying unknown internet access.

You use it like this.

```
sudo nethogs wlan0
```

Change wlan0 for the interface you are using. You can get a list of the interfaces using

```
ifconfig -s
```

It was designed to find out what is hogging your bandwidth.

Kind regards

---

### Post by CaptainofCrunch on 2012-02-23
> **matt_symes said:**
> Hi

When i need to see what is using my bandwidth, i use nethogs.

```
sudo apt-get install nethogs
```

It will give you a second by second account of what is using your bandwidth at that moment. Very easy to use and to see what is happening. Read the man page for it.

I have found it useful for identifying unknown internet access.

You use it like this.

```
sudo nethogs wlan0
```

```
ifconfig -s
```

It was designed to find out what is hogging your bandwidth.

Kind regards


That will definitely come in handy thank you.

I'm assuming that the values in the sent column are in bytes?

And is there any way to get it to display a continuous list instead of only 11 at a time?
Change wlan0 for the interface you are using. You can get a list of the interfaces using

---

### Post by matt_symes on 2012-02-23
> **CaptainofCrunch said:**
> That will definitely come in handy thank you.

I'm assuming that the values in the sent column are in bytes?

They should be in KB/s i think.

> 
And is there any way to get it to display a continuous list instead of only 11 at a time?

Not quite sure what you mean by this

> 
Change wlan0 for the interface you are using. You can get a list of the interfaces using

ifconfig -s will list all your interfaces apart from ones that are down.

```
matthew@matthew-Aspire-7540:~$ ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
lo        16436 0     10588      0      0 0         10588      0      0      0 LRU
wlan0      1500 0    123500      0      0 0        115067      0      0      0 BMRU
matthew@matthew-Aspire-7540:~$ 
```

If have three interfaces on my laptop. 

* eth0 which is my wired ethernet card
* lo which is the local loopback address.
* wlan0 which is my wireless card.

As i am currently connected wirelessly, i need to check the traffic going over my wireless interface. Do do that i use this command

```
sudo nethogs wlan0
```

It will then start nethogs and that will refresh the output every second and display transfer rates.

I have attached a screenshot of nethogs on my machine. It shows the current traffic over my wireless interface.

You can see, i have an ssh session open. I am running chromium browser and there is an unknown root process. This can be tracked down though.

Kind regards

---

### Post by CaptainofCrunch on 2012-02-23
> **matt_symes said:**
> 

Not quite sure what you mean by this 

When I ran a check in the update manager multiple results showed up in nethogs and the result for chromium disapeared.I thought that it showed the total amount of data used by each program not transfer speeds, but I understand now that the reason a program is removed from the list is because it is not using any data. 

Do you know is there anything out there that can give you a list of total data used per program? Like Onavo for Android devices 

[https://market.android.com/details?id=com.onavo.android.onavoid&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5vbmF2by5hbmRyb2lkLm9uYXZvaWQiXQ](https://market.android.com/details?id=com.onavo.android.onavoid&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5vbmF2by5hbmRyb2lkLm9uYXZvaWQiXQ)..


> **matt_symes said:**
> 

ifconfig -s will list all your interfaces apart from ones that are down.



in ifconfig -s I get eth0 and lo since I'm wired in with no wireless.

> **matt_symes said:**
> 

* lo which is the local loopback address.


What exactly is the lo?

---

### Post by matt_symes on 2012-02-23
> **CaptainofCrunch said:**
> When I ran a check in the update manager multiple results showed up in nethogs and the result for chromium disapeared.I thought that it showed the total amount of data used by each program not transfer speeds, but I understand now that the reason a program is removed from the list is because it is not using any data.

That is exactly correct.

> 
Do you know is there anything out there that can give you a list of total data used per program? Like Onavo for Android devices.

I would Google that ;)

> What exactly is the lo?

Actually i was a bit inexact; I should have said it was the local loopback interface and not address. 

It is the interface that the operating system (and any program) can use to talk to itself or another process on a local computer. It is not a hardware interface but a software interface.

As an example, you can use a browser to get web pages from an apache (or an other) web server when the browser and the web server are both on the same machine.

It's on the subnet is 127.0.0/16 but its usual address is 127.0.0.1. It is usually aliased as localhost in the hosts file.

```
matthew@matthew-Aspire-7540:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       matthew-Aspire-7540

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
matthew@matthew-Aspire-7540:~$
```

That enables you to type [noparse]http://localhost[/noparse] or [noparse]http://127.0.0.1[/noparse] into the web browser to get web pages from a web server on the same machine.

Kind regards

---

### Post by CaptainofCrunch on 2012-02-24
> **matt_symes said:**
> 
Kind regards

So it happened again to me this morning. I took screenshots so I'll attach it at the bottom.

It looks like chromium is what was causing the problem. The only page I had open was google.ie. I didn't have any sites uploading or downloading so why was it uploading at such high speeds?

---

### Post by matt_symes on 2012-02-24
Hi

> I didn't have any sites uploading or downloading so why was it uploading at such high speeds?

Do you have any extensions or plugins ? Maybe they were checking for updates ?

I have to be honest, i have no idea why chromium would do that. It is my preferred browser when in a GUI at the moment so i will keep a track on what mine is doing as well and report back to this thread if i see anything unusual.

In the meantime, i would suggest a bit of Googling.

BTW: If you find any apps that can give a total of usage for each application accessing the net on Ubuntu then please post back your results :D

Kind regards

---

### Post by CaptainofCrunch on 2012-02-24
> **matt_symes said:**
> Hi



Do you have any extensions or plugins ? Maybe they were checking for updates ?



The only extensions I have installed ar chrome to phone and springpad.

As for plugins I took screen shots so I'll attach them at the bottom. Do you know what that firsh one is 'Remote Viewer'. It doesn't sound too friendly and I don't remember installing it or anything like it.

> **matt_symes said:**
> 

BTW: If you find any apps that can give a total of usage for each application accessing the net on Ubuntu then please post back your results :D

Kind regards

Definitely if I find anything about such an app I will let you know

---

### Post by matt_symes on 2012-02-24
Hi

You could try a process of elimination and start disabling plugins and extensions and see if you get the traffic.

That may highlight what is generating the traffic. That would be my next move.

Kind regards

---

### Post by CaptainofCrunch on 2012-02-24
> **matt_symes said:**
> Hi

You could try a process of elimination and start disabling plugins and extensions and see if you get the traffic.

That may highlight what is generating the traffic. That would be my next move.

Kind regards

I will try that out and report back with results.

I haven't had any luck with the data usage app. I can't find anything on the web. I will keep looking, but maybe there isn't anything like this out there. I hope not.

Also do you know of any app that can limit my bandwidth? I tried wondershaper but when I put in values for 50k up and download, my actual speeds wouldn't go above about 300b. So I couldn't get it working. I also tried trickle but when I gave it values of 50k it would open a window for chrome and the speeds were normal, not limit at all.

So if you know of any app out there that can limit my bandwidth I would be much appreciated.

---

### Post by matt_symes on 2012-02-24
Hi

> Also do you know of any app that can limit my bandwidth? I tried wondershaper but when I put in values for 50k up and download, my actual speeds wouldn't go above about 300b. So I couldn't get it working. I also tried trickle but when I gave it values of 50k it would open a window for chrome and the speeds were normal, not limit at all.

So if you know of any app out there that can limit my bandwidth I would be much appreciated

Is this the total bandwidth for your PC ? I.E All applications will only be able to use up to a specific value ?

I have a friend of mine, who owns a guest house, wanted me to limit bandwidth on the range of ip addresses and for each of those ip addresses set the maximum upload and download limit to a defined value. (3M downoad 125K upload).

I used iptables rules to achieve this. Are you after something similar ? 

Kind regards

---

### Post by CaptainofCrunch on 2012-02-25
> **matt_symes said:**
> Hi



Is this the total bandwidth for your PC ? I.E All applications will only be able to use up to a specific value ?

I have a friend of mine, who owns a guest house, wanted me to limit bandwidth on the range of ip addresses and for each of those ip addresses set the maximum upload and download limit to a defined value. (3M downoad 125K upload).

I used iptables rules to achieve this. Are you after something similar ? 

Kind regards


Yes that's what I was trying to do. I want to limit the upload speed for the whole system if possible, I realize this might adversely affect some applications, so would it be possible to put a limit system wide and then give a few applications permissions to exceed the limit?

Also it happened again to me this morning. It was when I was watching a YouTube video, but it wasn't Chromium that was uploading it was something else. I took a screen shot. Do you know what that it?? **EDIT: I'm guessing is an IP 72.21.194.22 going it to port 80?**

For some reason its been happening more than usual lately. Maybe its because I'm more aware of it happening?

---

### Post by matt_symes on 2012-02-28
Hi

> **CaptainofCrunch said:**
> Yes that's what I was trying to do. I want to limit the upload speed for the whole system if possible, I realize this might adversely affect some applications, so would it be possible to put a limit system wide and then give a few applications permissions to exceed the limit?

Also it happened again to me this morning. It was when I was watching a YouTube video, but it wasn't Chromium that was uploading it was something else. I took a screen shot. Do you know what that it?? **EDIT: I'm guessing is an IP 72.21.194.22 going it to port 80?**

For some reason its been happening more than usual lately. Maybe its because I'm more aware of it happening?

Sorry for the delay in replying. It's been a busy weekend in my part of the woods.

I did a lookup on the ip address 72.21.194.22. This is what it returned.

```
matthew@matthew-Aspire-7540:~$ nslookup 72.21.194.22 8.8.8.8
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
22.194.21.72.in-addr.arpa       name = **s3-1.amazonaws.com**.

Authoritative answers can be found from:

matthew@matthew-Aspire-7540:~$ 
```

Not quite sure what that means though.

As for limiting bandwidth, i did it like this (using traffic control).

```
tc qdisc add dev br0 root handle 1: htb default 30;
tc class add dev br0 parent 1:0 classid 1:1 htb rate 3mbit ceil 3mbit;
tc filter add dev br0 protocol ip parent 1:0 prio 1 u32 match ip dst 192.168.1.100/32 flowid 1:1;

tc qdisc add dev br0 handle ffff: ingress;
tc filter add dev br0 protocol ip parent ffff: u32 match ip src 192.168.1.100/32 police rate 128kbit burst 10k drop flowid :1;
```

It's limited on IP address. 3M download and 128k upload (with some burst). You will need to change the IP address and other values as required.

As far as i am aware, there is no way to change it for different programs using this technique.

If you want this you will need to turn your firewall on.

Kind regards

---

### Post by CaptainofCrunch on 2012-02-28
> **matt_symes said:**
> Hi



Sorry for the delay in replying. It's been a busy weekend in my part of the woods.

I did a lookup on the ip address 72.21.194.22. This is what it returned.

```
matthew@matthew-Aspire-7540:~$ nslookup 72.21.194.22 8.8.8.8
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
22.194.21.72.in-addr.arpa       name = **s3-1.amazonaws.com**.

Authoritative answers can be found from:

matthew@matthew-Aspire-7540:~$ 
```

Not quite sure what that means though.



amazonaws.com is a is an amazon cloud storage site. I have Dropbox and Ubuntu One installed on this computer but Dropbox was not running at all and I'm pretty sure Ubuntu One wasn't running either. They are the only cloud storage apps I have. 

I looked  up other IP addresses that were uploading large amounts.

72.52.7.84 is from a site called prolexic.com which is "Prolexic is the world's largest and most trusted Distributed Denial of Service (DDoS) mitigation provider"

and

72.21.194.22 is for s3.amazonaws.com same as before, cloud storage.

Do you know what could be doing this? Or should I start a thread in security and see if anybody can help?

> **matt_symes said:**
> 

As for limiting bandwidth, i did it like this (using traffic control).

```
tc qdisc add dev br0 root handle 1: htb default 30;
tc class add dev br0 parent 1:0 classid 1:1 htb rate 3mbit ceil 3mbit;
tc filter add dev br0 protocol ip parent 1:0 prio 1 u32 match ip dst 192.168.1.100/32 flowid 1:1;

tc qdisc add dev br0 handle ffff: ingress;
tc filter add dev br0 protocol ip parent ffff: u32 match ip src 192.168.1.100/32 police rate 128kbit burst 10k drop flowid :1;
```

It's limited on IP address. 3M download and 128k upload (with some burst). You will need to change the IP address and other values as required.

As far as i am aware, there is no way to change it for different programs using this technique.

If you want this you will need to turn your firewall on.

Kind regards

How do I set this as a new IPtable?
What do I need to change? the IP and the values for uploading and downloading? 

Can this just be set for uploading or do I need to do both uploading and downloading?

Thank You for you help with all this aswell.

---

### Post by matt_symes on 2012-02-28
Hi

> **CaptainofCrunch said:**
> amazonaws.com is a is an amazon cloud storage site. I have Dropbox and Ubuntu One installed on this computer but Dropbox was not running at all and I'm pretty sure Ubuntu One wasn't running either. They are the only cloud storage apps I have. 

I looked  up other IP addresses that were uploading large amounts.

72.52.7.84 is from a site called prolexic.com which is "Prolexic is the world's largest and most trusted Distributed Denial of Service (DDoS) mitigation provider"

and

72.21.194.22 is for s3.amazonaws.com same as before, cloud storage.

Do you know what could be doing this? Or should I start a thread in security and see if anybody can help?

I would maybe start a new thread in security. See if anybody else has come across them.

> 
How do I set this as a new IPtable?
What do I need to change? the IP and the values for uploading and downloading?

The IP address needs to match the IP address on your PC. You can change the upload and download values to values that are good for you.

Just open a terminal and run the commands (edited for your set up). I'm not sure that you do need IP tables running for these commands (I'd had a couple of beers when i posted that post) as these are traffic control commands.

You can test it with an online speed checker.

They will not persist across reboots so you will need to create a script to run when the computer boots up.

> 
Can this just be set for uploading or do I need to do both uploading and downloading?

You can set it just for downloading if you want.

> 
Thank You for you help with all this aswell.

My pleasure.

Kind regards

---

### Post by matt_symes on 2012-02-28
Hi

As an addendum to my last post, it is possible to set up your firewall so it will drop connections to unwanted sites.

There is a tutorial on these forums for that somewhere. It could be adapted to drop connections to those IP addresses.

Kind regards

---

### Post by CaptainofCrunch on 2012-02-28
> **matt_symes said:**
> Hi



I would maybe start a new thread in security. See if anybody else has come across them.

[/QUOTE]

Ok I will do this now. Hopefully its nothing serious but better safe than sorry.

> **matt_symes said:**
> 

The IP address needs to match the IP address on your PC. You can change the upload and download values to values that are good for you.

Just open a terminal and run the commands (edited for your set up). I'm not sure that you do need IP tables running for these commands (I'd had a couple of beers when i posted that post) as these are traffic control commands.

You can test it with an online speed checker.

They will not persist across reboots so you will need to create a script to run when the computer boots up.



You can set it just for downloading if you want.



My pleasure.

Kind regards

I will try this when I get home and let you know how it goes.


> **matt_symes said:**
> 

Hi

As an addendum to my last post, it is possible to set up your firewall so it will drop connections to unwanted sites.

There is a tutorial on these forums for that somewhere. It could be adapted to drop connections to those IP addresses.

Kind regards



I will have a look for this aswell and hopefully it will help solve the problem.

Thank you.

---

