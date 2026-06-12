---
title: "remote control for 9.04"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Rapp3x on 2009-07-20
I'm pretty new to Ubuntu (have it sciens june) and wonder if it exists any remote controling services as Logmein or some other app that allows me to control the whole system and not just the terminal?

P.S I have gnome

---

### Post by alexlafreniere on 2009-07-20
Do you mean like a remote desktop type service? Any VNC client should work once you get it configured properly.

---

### Post by jamest09 on 2009-07-20
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

---

### Post by Rapp3x on 2009-07-20
How do I set up an VNC server then?

And the link to debian admin, if I would use that way I won't be able to acsess my computer from school because it needs an confirmation that the conection is allowed...

---

### Post by martinbaselier on 2009-07-20
You do not have to turn that option on. If you just follow the instructions in the provided link, you will have the vnc server set up.

---

### Post by doas777 on 2009-07-20
First a word of caution. there are a few ways to do what you want, but it is a little complicated, and the easier the method, the more unsafe it is. 

I would seriously caution you against exposing a vnc server to the internet, but you can use it with SSH to provide secure login.

---

### Post by superprash2003 on 2009-07-21
link posted at post no 3 is pretty good.. if you want to remote access it over the internet then you would need to open port 5900 in your router

---

### Post by Rapp3x on 2009-07-21
Thank's for all the answers and the link was good but not really what I was looking for "/

Then I searched The Mighty Google and found this
[http://imthi.com/blog/linux/ubuntu-904-remote-desktop-using-vncserver-without-monitor.php](http://imthi.com/blog/linux/ubuntu-904-remote-desktop-using-vncserver-without-monitor.php)
witch explanes things really good but it misses the part on how to acess from a windows system :P 

Thanks for all!

---

### Post by doas777 on 2009-07-21
if you want to access ubuntu "remote desktop" just use vncview (from tight or real VNC) and if you opt to use SSH, a copy of PuTTY as well. you can keep both on a thumbdrive, as they need no install.

---

### Post by Fdrock on 2009-08-14
Go to this thread:
[http://ubuntuforums.org/showthread.php?t=272986&highlight=logmein&page=10](http://ubuntuforums.org/showthread.php?t=272986&highlight=logmein&page=10)
I been using NTRconnect for the last few days without no problem
Hope it helps :)

---

### Post by MeumFidet on 2009-08-17
Hi all,

I have read your posts and am still having some difficulty - sorry, linux newbie!  

I have putty and tightvnc installed on my Vista system and want to connect to my Ubuntu 9.04 server to run a remote desktop session.  I can connect via putty with no problem but as my command line knowledge is still relatively small, the remote desktop seems to be a reasonable way of covering my options.

How do I start the ubuntu vnc service via putty? Assume I do not have physical access to my server (it is on my home network, so there are no port complications, but I want to practice accessing a remote server to host a web forum and will only have remote access).

I tried  "sudo vncserver :0" to but got the resonse "sudo: vncserver: command not found"
What am I doing wrong?

Thanks for any help!

MF

---

### Post by warreno on 2009-08-19
> **jamest09 said:**
> [http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

Howdy, all. I'm looking to do something similar here and the above link looks very promising.

However, I might have a bit of a kink in this one; the Lin box I want to connect to is online via DSL, as is mine. (The remote install belongs to some friends, and they occasionally need admin tasks performed, such as installing extra codecs for music or whatever. I haven't yet assigned sufficient privs to any user there to let that happen.)

I *believe* both systems have static IP addresses behind the DSL connection — actually I know mine does, since I get telephony provided by VoIP through the cable company, which requires a static IP to assign the phone number — but my question is how I get to the other Lin box. (Short of, you know, getting in the car, driving a while, getting out, etc.)

Put like this, my local machine's IP might be something like 192.168.foo.bar, while the remote machine's may be 192.168.bil.bo. OK, but in between there is another layer of IP that's providing the gateway to the net-at-large for both systems, if my understanding is correct. It may be something like 102.54.32.117, for instance.

So to connect to the remote Lin box, I'd have to somehow make a bridge from the general IP (102.54.32.117) to that system's local IP (192.168.bil.bo), correct? Is there a magic switch I can throw, or am I going to be spending a lot of time in terminal? That wouldn't particularly be a problem, but I'm not sure how to begin, or if  what I'd like to do is particularly feasible at all.

Or is it something stupidly simple, like connecting to 102.54.32.117:192.168.bil.bo?

Does anyone know of a HOWTO or something similar? I've Googled for what seems obvious to me ("connecting to linux by dsl", "remote linux connection", etc.) but nothing seems to really address what I need to do — or maybe I'm not looking in the right place.

Mille grazi for any suggestions.

---

### Post by MeumFidet on 2009-08-19
> **warreno said:**
> 
So to connect to the remote Lin box, I'd have to somehow make a bridge from the general IP (102.54.32.117) to that system's local IP (192.168.bil.bo), correct? Is there a magic switch I can throw, or am I going to be spending a lot of time in terminal? That wouldn't particularly be a problem, but I'm not sure how to begin, or if  what I'd like to do is particularly feasible at all.



hey warreno,

In my very limited undertanding, you would need to either configure IP forwarding on the remote router so that the NAT can translate your external/inbound request to an internal/inbound request, or... configure ssh and use Putty and command-line? 

HTH!  Cheers,  MF

---

### Post by warreno on 2009-08-19
That feels about right. There's also a port (5900) that needs to be opened to handle the commands. But I'm also concerned about security. I really don't want to chance leaving the system wide open. Requiring ssh and a password can help, but even still, well...

On another thread I saw you'd considered ebox and webmin. Did you try either one, and if so, what was your experience with them?

---

### Post by flatland2d on 2009-08-19
> **warreno said:**
> Howdy, all. I'm looking to do something similar here and the above link looks very promising.

However, I might have a bit of a kink in this one; the Lin box I want to connect to is online via DSL, as is mine. (The remote install belongs to some friends, and they occasionally need admin tasks performed, such as installing extra codecs for music or whatever. I haven't yet assigned sufficient privs to any user there to let that happen.)

I *believe* both systems have static IP addresses behind the DSL connection — actually I know mine does, since I get telephony provided by VoIP through the cable company, which requires a static IP to assign the phone number — but my question is how I get to the other Lin box. (Short of, you know, getting in the car, driving a while, getting out, etc.)

Put like this, my local machine's IP might be something like 192.168.foo.bar, while the remote machine's may be 192.168.bil.bo. OK, but in between there is another layer of IP that's providing the gateway to the net-at-large for both systems, if my understanding is correct. It may be something like 102.54.32.117, for instance.

So to connect to the remote Lin box, I'd have to somehow make a bridge from the general IP (102.54.32.117) to that system's local IP (192.168.bil.bo), correct? Is there a magic switch I can throw, or am I going to be spending a lot of time in terminal? That wouldn't particularly be a problem, but I'm not sure how to begin, or if  what I'd like to do is particularly feasible at all.

Or is it something stupidly simple, like connecting to 102.54.32.117:192.168.bil.bo?

Does anyone know of a HOWTO or something similar? I've Googled for what seems obvious to me ("connecting to linux by dsl", "remote linux connection", etc.) but nothing seems to really address what I need to do — or maybe I'm not looking in the right place.

Mille grazi for any suggestions.

This sounds like you wan a dynamic DNS.  This service will run on your computer (or router, depending on the model) and update your dynamic IP to a url you can access.  Here are some sites to check out.

[www.no-ip.com](www.no-ip.com)
[www.dyndns.com](www.dyndns.com)

For example: username.no-ip.org will point to 102.54.32.117 (or whatever your WAN IP is).

You would still need port forwarding on your router in order to connect to your 192.168.bil.bo computer.

---

### Post by stinger30au on 2009-08-19
[https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

---

### Post by warreno on 2009-08-19
> **stinger30au said:**
> [https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

Wow. Oh wow, that's an exciting looking tool … but I can't seem to get it past step 4 in its connection process. The "helper" package just stays in "listen" mode while the "sharer" package does detect the computer, but gives up after a while saying there's no route to the host — even if I've checked "Automatically handle firewall".

Dang. Do you know if this app pair relies on remote desktop being active? The docs on the website are, shall we say, minimal.

In any case thanks for passing along the link.

---

### Post by warreno on 2009-08-19
Hmm, dDNS doesn't seem to function as well as I'd hoped either (but thanks for posting the idea, **flatland2d**), and the more I think about it, the more I wonder *why* I would set it up since I really wouldn't have any use for it apart from remote admin access.

I have my own top-level domain already with very good tech support, so there'd be no reason for me to set up a dDNS server to host pages or what have you. At least none I can see right now.

So. If my understanding is correct about remote desktops, in order for me to browse the other person's system, s/he would have to have remote desktop running in client mode, correct?

But in order for me to do any remote admin level installs (such as drivers for audio playback), the target OS user would need to have admin access anyway *and* would have to enable remote desktop with admin privileges. (Or so I understand.) Which sort of defeats the purpose of restricting user access to the system commands that really truly could hose the OS.

And in any case, I don't like the idea of leaving port 5900 open to the world.

I'm thinking I'm just going to fall back on the old standby, the Bright and (Somewhat) Nerdy Teen. Fortunately there's one handy at the friends' house.*

I think I'll just add him to the admin group and issue a Stern Lecture about downloading *only* from trusted sources, and about *never* running commands in the terminal without knowing what they're supposed to do &#8212; and why. (I once lost an **entire Windows partition** under Slackware when I sloppily ran an [COLOR=DarkRed]rm -rf */[/COLOR] and forgot to unmount it first.**) Also I'll probably pass along a copy of the [*Ubuntu Pocket Guide*]("http://ubuntuforums.org/showthread.php?t=1052065").

If he gets in a bind, after all, he just has to pick up the phone and follow along.

====

* I set up their system with an admin account and one for each user &#8212; four users. He was the only one who changed his password, and he figured out how to do it on his own despite having only used XP prior to that, with GNOME being brand new to him, as in the very same afternoon. Not bad.

He's the one getting into issues now since I neglected to install the necessary extra drivers for burning audio discs from Amarok. I think he can be trusted with some admin rights, and I think he probably deserves them.

** I'm sure you're thinking *no big loss there*, but this was 14 or so years ago when Slackware was useful to few others but engineers, and Windows was really the only other GUI option for PCs apart from OS\2 Warp. (Which, BTW, was a *fantastic* OS. I love Mah Jongg Solitaire to this day.) I didn't even have a CD-ROM; all installs were done from floppy. So, you know, ouch.

---

### Post by flatland2d on 2009-08-20
> **warreno said:**
> Hmm, dDNS doesn't seem to function as well as I'd hoped either (but thanks for posting the idea, **flatland2d**), and the more I think about it, the more I wonder *why* I would set it up since I really wouldn't have any use for it apart from remote admin access.

I have my own top-level domain already with very good tech support, so there'd be no reason for me to set up a dDNS server to host pages or what have you. At least none I can see right now.

So. If my understanding is correct about remote desktops, in order for me to browse the other person's system, s/he would have to have remote desktop running in client mode, correct?

But in order for me to do any remote admin level installs (such as drivers for audio playback), the target OS user would need to have admin access anyway *and* would have to enable remote desktop with admin privileges. (Or so I understand.) Which sort of defeats the purpose of restricting user access to the system commands that really truly could hose the OS.

And in any case, I don't like the idea of leaving port 5900 open to the world.

I'm thinking I'm just going to fall back on the old standby, the Bright and (Somewhat) Nerdy Teen. Fortunately there's one handy at the friends' house.*

I think I'll just add him to the admin group and issue a Stern Lecture about downloading *only* from trusted sources, and about *never* running commands in the terminal without knowing what they're supposed to do — and why. (I once lost an **entire Windows partition** under Slackware when I sloppily ran an [COLOR=DarkRed]rm -rf */[/COLOR] and forgot to unmount it first.**) Also I'll probably pass along a copy of the [*Ubuntu Pocket Guide*]("http://ubuntuforums.org/showthread.php?t=1052065").

If he gets in a bind, after all, he just has to pick up the phone and follow along.

====

* I set up their system with an admin account and one for each user — four users. He was the only one who changed his password, and he figured out how to do it on his own despite having only used XP prior to that, with GNOME being brand new to him, as in the very same afternoon. Not bad.

He's the one getting into issues now since I neglected to install the necessary extra drivers for burning audio discs from Amarok. I think he can be trusted with some admin rights, and I think he probably deserves them.

** I'm sure you're thinking *no big loss there*, but this was 14 or so years ago when Slackware was useful to few others but engineers, and Windows was really the only other GUI option for PCs apart from OS\2 Warp. (Which, BTW, was a *fantastic* OS. I love Mah Jongg Solitaire to this day.) I didn't even have a CD-ROM; all installs were done from floppy. So, you know, ouch.

Regarding remote access with admin privileges, why can't you sudo everything even while logged in on a restricted account?  There's nothing you have to do to run remote desktop with admin privileges.  It's the same as if you're sitting there in front of the computer.

There's some way to run VNC through SSH, which would help your security concerns, but I have not tackled that yet so I can't help there.

---

### Post by MeumFidet on 2009-08-20
> **warreno said:**
>  
On another thread I saw you'd considered ebox and webmin. Did you try either one, and if so, what was your experience with them?
 
HI Warreno,
 
I looked at several threads that suggest webmin is very unstable on unbuntu - the last thing I need is unexplained results! So I tried ebox.  Ahem.  Yep unexplained results too... I installed ebox on both a 9.04 desktop system and a 9.04 server system (just to compare results as the desktop system is gui and I can more easily see what is happening).  
 
I used synaptic on the desktop and apt-get install ebox onthe server (via ssh) and got completely different results.  Both ebvox systems are up and running, but the desktop has most of the modules installed whereas I had to "apt-get install ebox-openvpn" to install the extra modules I needed on the server.
 
As yet, neither system will let me switch on the vpn server, despite creating security certificates, so I am not really much better off! Ho hum.  Lol, it's a vertical learning curve! 
 
Anyhoo, I will watch with interest.  Cheers, MF

---

### Post by warreno on 2009-08-20
> **flatland2d said:**
> Regarding remote access with admin privileges, why can't you sudo everything even while logged in on a restricted account?  There's nothing you have to do to run remote desktop with admin privileges.  It's the same as if you're sitting there in front of the computer.

There's some way to run VNC through SSH, which would help your security concerns, but I have not tackled that yet so I can't help there.

Seems that sudo won't work, in a restricted account, when running installs via Add/Remove or through a similar GUI. That is, if I'm logged in to a restricted account on that machine and try to load something that can alter the system, it won't accept my admin password in that restricted user's account *through the GUI install tools*.

Sure, it can work in the terminal, but I'm not looking at terminal access for a lot of this anyway; besides, I still have that open-port security issue to vex me. And vex me it does; lo, I wax most vexed by it.

The other problem is that I'm not actually connected to the target machine on a LAN or even a WAN via a fixed pair of IPs. There's ssh, but there's no HTTPS, and I have no way of knowing what kind of packet security our respective ISPs or our dDNS go-betweens might be running. That's an issue because I killed XP once and for all on their box after they got that "Security Shield" virus/trojan/phish a couple weeks back.* So re-opening their system to possible attack now would seem inadvisable. There are too many potential security holes here.

It is vexing.

I think I'd rather spend a few hours teaching a bright seventeen-year-old how to do things that will probably serve him well later on in life, than try to cruft my way around something that seems to be dodgy at best, with limited probable success, for very little actual payoff.

====

* That was a nasty one. At login, a program would load claiming it was looking for viruses, then claim it had found dozens of infected files. Conveniently, Add/Remove Programs (in XP) was one of the "infected" files it refused to let load. It then squatted and held the system hostage until a credit card number was entered to pay for the "full" version. This bugger got around both Norton and AVG.

I fully favor the idea of summary execution for all virus authors.

---

