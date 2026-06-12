---
title: "Can't access specific websites in Linux"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Rhodophyta on 2010-11-22
Hello,
I am running Linux Mint and Windows 7 on my Compaq Presario CQ60. I am having a strange problem--I am unable to connect to certain secure university sites. One of them should take me to the library catalog, and the other should take me to my STAR degree check after I've logged into the secure system. Here are the two urls:
[http://uhmanoa.lib.hawaii.edu:7008/vwebv/searchBasic?sk=manoa](http://uhmanoa.lib.hawaii.edu:7008/vwebv/searchBasic?sk=manoa)
[https://lum46.its.hawaii.edu:8008/cpipconnector/kuhi/Pickup?sid=/HjtSysDg3InCz0ZEJRHSA__&url=star-stu](https://lum46.its.hawaii.edu:8008/cpipconnector/kuhi/Pickup?sid=/HjtSysDg3InCz0ZEJRHSA__&url=star-stu)

Both of the url's have a : in them...could that be the problem? I've tried to access from home and from the school network. My husband can reach the sites just fine on our network from his Windows machine, and I can reach them on any browser when I boot mine into Windows. I've tried both Chrome and Firefox in Linux.

EDIT2: I can reach these websites when I boot into Windows 7 on the same machine, on any browser, for clarification.
EDIT: You will not be able to access the second site because it requires logging into the school system first (which I can do easily). I only included it in case there was something in the url that someone can see causing problems.

I don't have a firewall or IP blocker enabled. I'm thinking this is probably a very simple problem but I don't know how to fix--I've already cleared my cache, etc.

Thanks so much!

---

### Post by grahammechanical on 2010-11-22
I can get on to the Hawii voyager basic search page by clicking on your link but the other link just brings up a blank page. That could be because a person would need to log in to the site first of all before going to the page you have put a link to.

Regards

---

### Post by Rhodophyta on 2010-11-22
Yes, I always log into the UH system first before trying to access the degree check link. So most people won't be able to get to it. I only included it in case there was something obvious in the url that would cause problems. I'll edit the OP to clarify.

And yes, I'm sure most people can connect to the library voyager site, but I can't on my machine when booted into Linux, no matter what browser or network I'm on. That's the problem :)

---

### Post by grahammechanical on 2010-11-22
You do not say if you can connect when using windows 7. Can You? If you can't, then the only thing that I can think off is some kind of security setting in the BIOS. Is there this feature in a BIOS? I do not know.

regards.

---

### Post by Rhodophyta on 2010-11-22
Yes, as stated in my first post, I can access these sites when I boot into Windows (7), but not when I boot into Linux. I'll edit the OP again to clarify. Thank you for your time.

---

### Post by Rhodophyta on 2010-11-27
Bumping in case anyone has additional suggestions...it's not the end of the world to restart and boot into Windows whenever I need to access school stuff, but it would be really nice to be able to do it from Linux. Thanks!

---

### Post by SeijiSensei on 2010-11-27
Have you spoken to the university's IP department?  Maybe they don't support Linux.  Perhaps the site requires that the connecting browser be Internet Explorer?  (Can you connect with both IE and Firefox from Windows 7?)

You can use the Firefox add-on called "[user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/")" so that your browser will send a User-Agent string that makes it appear to be running IE on Windows.

---

### Post by dondiego2 on 2010-11-27
> **SeijiSensei said:**
> Have you spoken to the university's IP department?  Maybe they don't support Linux.  Perhaps the site requires that the connecting browser be Internet Explorer?  (Can you connect with both IE and Firefox from Windows 7?)

You can use the Firefox add-on called "[user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/")" so that your browser will send a User-Agent string that makes it appear to be running IE on Windows.


It's obviously not on the University's end if we can all get to the website using Linux.  I'm on Ubuntu and using Firefox and had no problem accessing the first site.

You say you've tried it Firefox and Chrome on Linux right?  Can you ping the site using a terminal?  I'm not too terminal savvy but there people on this site that should be able to help you trouble shoot this.

---

### Post by Rhodophyta on 2010-11-27
I just typed in ```
ping http://uhmanoa.lib.hawaii.edu:7008/vwebv/searchBasic?sk=manoa
```

But it returned "unknown host". Did I do this correctly?

Also, I'm pretty sure that I was able to access the websites the last time I tried, which would have been around August. Don't know if that makes a difference. Maybe some update screwed it up? But why would it affect only those two sites that I know of?

Also, yes, if others can get to the website than it is something with my particular computer. I've tried Chrome and Firefox in Linux with no success, but I can access these sites in Windows using Chrome, IE, or Firefox.

I wonder...the : thing in the url is unusual, right? Does anyone have any other urls with a colon in them so I can try them out?

Edit: And the university's tech support is absolutely useless :) They can only offer support to Windows and IE reliably.

---

### Post by dondiego2 on 2010-11-27
After I posted I tried pinging the site just like you did and it came back the same as you got back.  I tried pinging Google just to make sure and Google answered back.  Although I can access the library web site through Firefox on my computer so I'm about at the limit of my knowledge, but I will ponder it a bit more.

---

### Post by dondiego2 on 2010-11-27
Try this and see what comes back in a terminal

```
ping -c5 www.uhmanoa.lib.hawaii.edu
```

---

### Post by Rhodophyta on 2010-11-27
It returned ```
tara@tara-laptop ~ $ ping -c5 www.uhmanoa.lib.hawaii.edu
PING www.uhmanoa.lib.hawaii.edu (24.28.193.9) 56(84) bytes of data.
64 bytes from tr-ssl.rr.com (24.28.193.9): icmp_seq=1 ttl=44 time=144 ms
64 bytes from tr-ssl.rr.com (24.28.193.9): icmp_seq=2 ttl=44 time=128 ms
64 bytes from tr-ssl.rr.com (24.28.193.9): icmp_seq=3 ttl=44 time=125 ms
64 bytes from tr-ssl.rr.com (24.28.193.9): icmp_seq=4 ttl=44 time=192 ms
64 bytes from tr-ssl.rr.com (24.28.193.9): icmp_seq=5 ttl=44 time=133 ms

--- www.uhmanoa.lib.hawaii.edu ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 125.004/144.701/192.094/24.578 ms
```

When I actually try to navigate to  [http://www.uhmanoa.lib.hawaii.edu/](http://www.uhmanoa.lib.hawaii.edu/) I can't, though--it says chrome can't find it (nor can firefox). Odd?

---

### Post by dondiego2 on 2010-11-27
Yes I'm finding it odd too.  I can't navigate to it but I can ping it.  I can navigate to the site you provided but I can't ping it.  Back to the drawing board.

---

### Post by dondiego2 on 2010-11-27
Try this

```
ping -c5 uhmanoa.lib.hawaii.edu
```

I was able to ping it and by putting that (uhmanoa.lib.hawaii.edu) into a web browser (Firefox) it took me to the site.

---

### Post by davec64 on 2010-11-27
Just to add to the mix, the ":" followed by a number id the port number being used by the web server at that end. Normally for http it's port 80, bu8t for some reason the IT Dept are using other ports.

Just a thought, your linux system isn't blocking those outgoing ports is it?
I'm afraid I wouldn't know where to look though :-|

---

### Post by Rhodophyta on 2010-11-27
The ping returned some wierdness:
```
tara@tara-laptop ~ $ ping -c5 uhmanoa.lib.hawaii.edu
PING end2.lib.hawaii.edu (128.171.19.17) 56(84) bytes of data.
From tara-laptop.local (192.168.1.4) icmp_seq=1 Destination Port Unreachable
From tara-laptop.local (192.168.1.4) icmp_seq=2 Destination Port Unreachable
From tara-laptop.local (192.168.1.4) icmp_seq=3 Destination Port Unreachable
From tara-laptop.local (192.168.1.4) icmp_seq=4 Destination Port Unreachable
From tara-laptop.local (192.168.1.4) icmp_seq=5 Destination Port Unreachable

--- end2.lib.hawaii.edu ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4005ms

```

And I tried to navigate to uhmanoa.lib.hawaii.edu in both Chrome and Firefox, but no luck! When I pasted into my url bar, it redirected to [http://uhmanoa.lib.hawaii.edu:7008/vwebv/searchBasic?sk=manoa](http://uhmanoa.lib.hawaii.edu:7008/vwebv/searchBasic?sk=manoa) (the original site I was having problems with) and it couldn't be reached.

---

### Post by dondiego2 on 2010-11-27
That points to a port problem I'm thinking like the last poster said.  Is there a firewall blocking it?

Here is what I get

```
carl@carl:~$ ping -c5 uhmanoa.lib.hawaii.edu
PING end2.lib.hawaii.edu (128.171.19.17) 56(84) bytes of data.
64 bytes from end2.lib.hawaii.edu (128.171.19.17): icmp_req=1 ttl=238 time=145 ms
64 bytes from end2.lib.hawaii.edu (128.171.19.17): icmp_req=2 ttl=238 time=145 ms
64 bytes from end2.lib.hawaii.edu (128.171.19.17): icmp_req=3 ttl=238 time=147 ms
64 bytes from end2.lib.hawaii.edu (128.171.19.17): icmp_req=4 ttl=238 time=143 ms
64 bytes from end2.lib.hawaii.edu (128.171.19.17): icmp_req=5 ttl=238 time=145 ms

--- end2.lib.hawaii.edu ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 143.745/145.299/147.387/1.175 ms
```

---

### Post by Rhodophyta on 2010-11-27
> **davec64 said:**
> Just to add to the mix, the ":" followed by a number id the port number being used by the web server at that end. Normally for http it's port 80, bu8t for some reason the IT Dept are using other ports.

Just a thought, your linux system isn't blocking those outgoing ports is it?
I'm afraid I wouldn't know where to look though :-|

You just set off a lightbulb in my head.

Yes, I have some outgoing ports blocked when I am using Transmission. I turned off transmission and now I can access the sites. I thought it wouldn't be an issue because I have IPblock turned off, but there are some settings within Transmission that must be causing the problem.

I feel like an idiot! I knew it would be something simple like this!

Thank you sincerely to everyone for their help!!

---

### Post by adamjkok on 2010-11-27
> **Rhodophyta said:**
> I just typed in ```
ping http://uhmanoa.lib.hawaii.edu:7008/vwebv/searchBasic?sk=manoa
```But it returned "unknown host". Did I do this correctly?

Also, I'm pretty sure that I was able to access the websites the last time I tried, which would have been around August. Don't know if that makes a difference. Maybe some update screwed it up? But why would it affect only those two sites that I know of?

Also, yes, if others can get to the website than it is something with my particular computer. I've tried Chrome and Firefox in Linux with no success, but I can access these sites in Windows using Chrome, IE, or Firefox.

I wonder...the : thing in the url is unusual, right? Does anyone have any other urls with a colon in them so I can try them out?

Edit: And the university's tech support is absolutely useless :) They can only offer support to Windows and IE reliably.

The colon in the URL is the port number (7008 ) The reason is that the browser assumes that the port number is 80 for HTTP and (I think, correct me if I'm wrong) 443 for HTTPS, so anything else must be explicitly specified. Right now, you're actually on ubuntuforums.org:80, but the :80 is hidden to avoid confusion.

Additionally, I forget the exact reason even though I've been told why, you can't ping on a specific port. Try:
```
ping uhmanoa.lib.hawaii.edu
```HTH

---

### Post by davec64 on 2010-11-27
> **Rhodophyta said:**
> You just set off a lightbulb in my head.

Yes, I have some outgoing ports blocked when I am using Transmission. I turned off transmission and now I can access the sites. I thought it wouldn't be an issue because I have IPblock turned off, but there are some settings within Transmission that must be causing the problem.

I feel like an idiot! I knew it would be something simple like this!

Thank you sincerely to everyone for their help!!

Glad to have set the bells ringing!
It always the same, you can't see the wood for the trees when you've got a problem! :D

---

