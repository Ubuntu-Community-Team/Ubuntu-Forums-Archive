---
title: "Stop all network traffic if PPTP VPN disconnects?"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Beardednerd on 2011-02-16
Hello, I  use a PPTP VPN for privacy and bittorrent. I have been over all very happy, only taking about a 1/4 hit to my over all network speed. However, I recently downgraded my VPN package, and the new sever I connect through is sometimes unstable with a high throughput. Because of this I am trying to find a way to block ALL (HTTP, bittorrent, email, etc) outgoing network traffic when the VPN fails, and then resume the traffic when the VPN reconnects. Essentially forcing all data through the VPN, and creating the illusion of simply having no network connection to the outside world at all when the VPN is offline/re-connecting. This is opposed to the current situation when the VPN will fail, all my traffic will switch to direct (visible) access through my ISP, and the VPN will re-establish sometime later (2-3mins, normally. Unless I manually restart it sooner).

Can this be done? I have tried Google, but have only been finding information on configuring local web access outside of the VPN for the sake of speed. Information of which I cannot seem to find a way to apply to this.

- BN

---

### Post by caen1944 on 2011-04-16
Hi,

I wish I could help but I am searching for an answer for exactly the same thing. 

Sadly, this is actually trivial to do with the windows vista firewall, but I can't figure out how to do this in linux. I hate resorting to windows for anything but playing games, but in this case...

There must be a way. I think that a manual connection to the VPN plus editing of the routing tables ought to do it, but I can't quite figure out how.

---

### Post by Cs0hu on 2012-02-19
I don't know if this will help so don't flare me if its not what you need, its the first time ever i post something here, i had a similar problem where i wanted to disconnect or at least kill a process when the vpn disconnects ... been looking all over google and duck for two days and i finally pieced together something that works for me (i use ubuntu 10.04 64 bit)

in case of guru : it's probably not the most elegant solution but this works for me without having to dig into the shattered bible of linux firewalls. If you don't want your traffic running wild over an unreliable connection while you're not present it might help

the script needs cleaning but if you like it can help you check the parameters that are passed in your logfile, turns out network manager calls all scripts in /etc/NetworkManager/dispatcher.d/

i never wrote a shell script before so i'm always open to suggestions for improvement
this one kills an application immediately when the vpn connection goes down, you can replace the 'java' probably with whatever needs killing at the moment in your case, i would like to completely disconnect but i dont know the command for that so here goes :

#!/bin/sh
# use tail - /var/log/syslog  in terminal to check if it is executed the four lines help you spot easily

logger -s XXXXXXXXXX
logger -s $1
logger -s $2
logger -s XXXXXXXXXX

if [ $2 = "vpn-down" ]
then
[COLOR=Red]ip link set wlan0 down[/COLOR]   #this will turn off your wireless networking completely in case you want that if not cross it out
killall java
fi

i hope this helps, i'm a bit disappointed and pretty much overwhelmed by how much  info there is on ubuntu alone, seems like a lot is outdated, if anyone finds this useful pls let me know if it works for you as well, thanks

[COLOR=Red]2nd edit : did a litlle more digging since my head is in the zone and  found how to shut the wlan0 (wifi) down while at it ... can # out lines  you don't need , i dont think most ppl here need it but ppl like me  might[/COLOR], hope im not supposed to rewrite the whole post sorry for the slop

edit : i probably should mention in case other people are as nub as me : chmod the script to 755 owernship root , and the scripts in the folder are executed in alphabetical order whenever there's a change in the state of a network interface (as far as i could figure that out from all the different sources)  so if you place multiple scripts its best to start the name with 00name 10name 90name etc in the order you want them to execute

---

### Post by coilwinder on 2013-03-12
[COLOR=#000000]Cs0hu, thanks for posting that! (Old thread I know but it helped me)

I'm also using Ubuntu 10.04 64-bit (LTS) on one of my linux boxes. Pretty new to vpn, and the one I got is pretty stable, but a couple of times now the connection just continued on the default network connection after vpn failed... not really what I wanted!

I changed your script a bit, so it simply kills the network. So it's a bit manual to get to work again. Well basically just right-click the network icon - disable then enable again network, then connect vpn, done.

[/COLOR][COLOR=#000000]By no means an expert in scripting myself either btw. [/COLOR][COLOR=#000000]I just tried it once now (in case this is somehow inaccurate, IE not really tested a lot), and it seems to work.[/COLOR][COLOR=#000000]

(And ofc, chmod to 755 as root, put in the [/COLOR][COLOR=#000000]/etc/NetworkManager/dispatcher.d/ directory)
[/COLOR][COLOR=#000000]

[/COLOR]```
#!/bin/sh
# use tail - /var/log/syslog in terminal to check if it is executed the four lines help you spot easily

logger -s XXXXXXXXXX
logger -s $1
logger -s $2
logger -s XXXXXXXXXX


if [ $2 = "vpn-down" ]
then
# Shut down eth0 when vpn fails (change eth0 to your nic)
ifconfig eth0 down
# this will turn off your wireless networking completely
# ip link set wlan0 down 
fi



```[COLOR=#000000]

[/COLOR]

---

