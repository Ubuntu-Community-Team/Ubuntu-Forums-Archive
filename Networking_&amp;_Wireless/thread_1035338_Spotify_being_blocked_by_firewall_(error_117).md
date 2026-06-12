---
title: "Spotify being blocked by firewall (error 117)"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by Nevon on 2009-01-09
For some reason Spotify is being blocked by the firewall (I guess). At first I thought it was because of the router (we recently installed it), but I can use Spotify just fine in Windows, so that can't be it. 

Spotify normally uses the port 4070 for login and streams. It also uses a bunch of different ports in the range of 14000 to 65000 for peer-to-peer action, however, Spotify seems to work even if you don't enable those. 

So how do I check if 4070 is blocked or not? And how would I go about to unblock it? It can't be a router setting, since it works fine in Windows, right?

---

### Post by Nevon on 2009-01-10
Come on, someone must know this.

---

### Post by Yma on 2009-03-21
Hi,

I have had several problem with my ubuntu 8.10 and internet connection, and one of them was the error 117 from the spotify application. I also had problem with internet speed during browsing. But when I was connected to my pc at work via vpn connection, all of these problem just disappered. I just got it to work now without the vpn connection active, so no spotify work perfectly and surfing the net with full speed :-).

Here is what I did:
I just open "Network configuration" -> wireless tab...Did some editing such as disable dhcp ( connect manually ), under select system configuration instead of automatic connection -> all of these changing did nothing for me so I just set it back to its "normal" state, and guess what...I NOW WORKS!! Why?? I dont know, i just does so I intend to leave it that way....

How you get your error 117 to work as well, Yngve

---

### Post by Yma on 2009-03-22
I have now located the problem. It seems it was the /etc/resolv.conf file that caused the problem. In my file I had these configuration....
....
nameserver 10.1.1.10
nameserver 192.168.1.1
...

The first one is to my office (use vpn), and the second one is my local network. After connected to internet this file is written by det resolvconf tool. If I change the order of these to nameservers in the /etc/resolv.conf file, it fixed my problem. The problem is that this file is overwritten every time you connects to internet and I had to manually change the order to get it to work. First I created a script that did the job for me, but it just became a heck. To get it to work permanently I just used the synaptic package manager and removed the resolvconf package - and now it works every time :-)

Yngve

---

### Post by nosegoblin on 2009-03-23
Wow! Thanks, it really did solve the problem! :D I had the same error 117 with spotify and just by changing the networking settings from dhcp to static and then back again solved the issue.

---

### Post by Zemren on 2009-07-15
Hi i have the same problem in 8.10 and the tips given here did not help me, does anyone have any other tips?

Thanks

---

### Post by Fake Dog on 2009-07-27
To configure your firewall, you can use Firestarter. Open a terminal and type

```
sudo aptitude install firestarter
```

Once it's installed, you'll find it in the applications menu under Internet, or by typing "sudo firestarter" into a terminal.

After the first-run configuration, you should click "Firewall" in the menu bar and "Stop Firewall". If Spotify works now, you know it's because of the firewall. If not, then it's not a firewall problem. If it works, start the firwall again so you can narrow down the problem. It's just a matter of opening the right ports.

In the Events tab, you can see if anything has been blocked. Open Spotify and see if this starts to fill up.

If you want to open any ports, click on the policy tab, then click in the second box down (with Allow Service | Port | For) on the top of it. Make sure you are editing "inbound traffic policy". Click "Add Rule" and type in the port number. Don't select any name as this gives predefined ports. The comment is for your own purposes, so just type in "Spotify" so you remember what it's for.

If it doesn't work now, try some of the ports from the Events tab until it works!

---

### Post by Nevon on 2009-08-05
> **Fake Dog said:**
> To configure your firewall, you can use Firestarter. Open a terminal and type

```
sudo aptitude install firestarter
```

Once it's installed, you'll find it in the applications menu under Internet, or by typing "sudo firestarter" into a terminal.

After the first-run configuration, you should click "Firewall" in the menu bar and "Stop Firewall". If Spotify works now, you know it's because of the firewall. If not, then it's not a firewall problem. If it works, start the firwall again so you can narrow down the problem. It's just a matter of opening the right ports.

In the Events tab, you can see if anything has been blocked. Open Spotify and see if this starts to fill up.

If you want to open any ports, click on the policy tab, then click in the second box down (with Allow Service | Port | For) on the top of it. Make sure you are editing "inbound traffic policy". Click "Add Rule" and type in the port number. Don't select any name as this gives predefined ports. The comment is for your own purposes, so just type in "Spotify" so you remember what it's for.

If it doesn't work now, try some of the ports from the Events tab until it works!

That's the weird part. I've tried disabling the firewall, and it still doesn't work. However, it works just fine on some networks. The only place I've found it to not work is at home, and only when running Linux. In Windows (or even Windows in VirtualBox, on a Linux host) it works just fine. :S

---

### Post by Andysan on 2009-08-18
Hi,

Has anyone been able to progress further with this please and come up with a  solution?

I ran Spotify on my Ubuntu PC under Wine for a few weeks, then put it on my Ubuntu laptop and since then both give me the 177 error..

I have followed the instructions posted and got Spotify to load once and only once by disabling the firewall.  Aside from this one time nothing has worked.

Can anyone offer any advice please?

Thanks,

Andy

---

### Post by tonychar on 2009-08-19
Hi, this worked for me, after reading and trying various "fixes" that didn't.

Untick the 'remember me' box, and add your password manualy.

It really was that simple for me.  Good luck,

Tony

---

### Post by C-Sauron on 2009-09-13
I've tried all solutions on this thread, but the problem persists and I can't login to Spotify. I've installed the Firestarter firewall, and it doesn't block any event when I try to login to Spotify. I've googled this problem for more than 2 hours and I can't find an effective fix.

Can somebody help me, please? :)

---

### Post by Andysan on 2009-09-13
> **C-Sauron said:**
> I've tried all solutions on this thread, but the problem persists and I can't login to Spotify. I've installed the Firestarter firewall, and it doesn't block any event when I try to login to Spotify. I've googled this problem for more than 2 hours and I can't find an effective fix.

Can somebody help me, please? :)

Ditto, has anyone had any success please?

---

### Post by Nevon on 2009-09-13
I have now moved, and as such I am now on a new network and everything is working fine on exactly the same hardware and with the same software.

---

### Post by stupidchunk on 2010-02-13
I have this problem too. Did everything stated in the thread but nothing worked. I even reinstalled Spotify to no avail. Anyone?

---

### Post by BeerFreek on 2011-02-24
Hi all just to say that I had this problem for several weeks and couldn't find a solution until yesterday. 

my web browser was slow in loading webpages even though my internet was fine, ping times and downloading were normal

So I remember to change DNS servers on my connection and voila, spotify started to working seamessly under wine again

[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)   <- a list of free dns to user

---

### Post by erlendkj on 2011-03-03
I've also experienced the 117 error problem. What worked for me was connecting to the internet through a VPN. I'm using cisco systems vpn client, however it seems there is an option for this in the networks menu that drops down from the panel.

---

