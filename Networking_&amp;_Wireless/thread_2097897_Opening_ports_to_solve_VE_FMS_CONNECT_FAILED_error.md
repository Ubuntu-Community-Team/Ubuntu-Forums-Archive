---
title: "Opening ports to solve VE_FMS_CONNECT_FAILED error"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2012-12-24
I'm running Kubuntu 12.10, and I've been having a persistent but apparently unusual problem: when I try to view Flash videos, I get the error **VE_FMS_CONNECT_FAILED**.  Other videos such as YouTube are OK; in fact, on the NYTimes site, there are videos with preceding commercials where I can view the commercial but not the content!

I found this explanation of the error in the BrightCove forum:
> This is the result of the Flash Media Server (FMS) being unable to establish a connection over port 1935; 443; and 80 leading to a connection timeout.

However, **ufw** tells me that the firewall is inactive and **iptables** has no entries. I've not done anything to configure either the firewall or the ports.  I get this both with Chrome and Firefox, so it seems to be unrelated to the browser.

Assuming the BrightCove explanation is correct, is there anything I can do about it?

---

### Post by Dave212 on 2013-03-30
I too have had this problem for a while, both with Firefox and Chrome.  The Solution, at least for my situation, seemed to be to change the MTU setting under the Network Connections.  For 11.10 go to the menu bar and pick
Applications[INDENT]Other[/INDENT]
[INDENT=2]Network Connections
[/INDENT]
[INDENT=3]<pick Wired, Wireless or whatever you are using>[/INDENT]
[INDENT=3]<select the name of the active connection, probably the most recently used>[/INDENT]
[INDENT=2]  press the Edit... button
change the MTU value.  Mine was set to Automatic so I changed it to 1492 bytes.  (Not sure what the optimum value would be.)
click Save...
[/INDENT]

Hope that helps.

---

### Post by pwabrahams on 2013-04-02
I changed the MTU value some time ago to 1492.  Alas, it didn't help.

---

### Post by Dave212 on 2013-04-14
Oh crud... This week changing the MTU value isn't working, at least for the site I am trying to view.  Looking at other forums and tech support FAQs, I see the problem spanning all platforms and many browsers.  

I can view the videos on my MacBook running Firefox.

Some videos fail on my Dell with Ubuntu 11.10 running Firefox and Chrome, and the same ones fail on my HP with Ubuntu 12.10 running Firefox and Chrome.

They all play the advertisement before the main video just fine.  

It looks like the thing common to all the platforms and browsers is the problem videos are served up by **Brightcove.com**.
The have a debugger at [http://admin.brightcove.com/viewer/BrightcoveDebugger.html](http://admin.brightcove.com/viewer/BrightcoveDebugger.html)
but it doesn't give much more information than what shows up in the error window in the video.

It looks like this problem, or various similar ones, have been occurring for a few years.  Too bad it is intermittent enough to not rise to the level that Brightcove seems to be able to reproduce and solve.  They do come across as having a rather poor customer service attitude.  And their customers are the media outlets.  I don't see an obvious way for end users to alert Brightcove to the problems other than contacting the video providers.

By the way, my ufw is inactive also.

---

### Post by Dave212 on 2013-04-14
Doing more sniffing around l ran across a posting on an Apple forum mentioning browser add-on conflicts.  I did a test by enabling and disabling various add-on and reloading the video page many times.

In Firefox pick 
    Tools 
pulldown and select 
    Add-ons
of course Shockwave Flash should be Enabled

I also have plug-ins for:
DivX Web Player
QuickTime Plug-in 7.6.6 (abbreviated QT below)
VLC Multimedia Plugin (compatible Totem 3.0.1) 
Windows Media Player Plug-in 10 (compatible; Totem) (abbreviated WMP)

Video **does not** work with:
    Sw only  (but plays ad)
    Sw and DivX (plays ad)
    Sw and QT (plays ad)
    Sw and WMP (plays ad)
        
     Sw, VLC, and QT (fails right away, or plays only the ad, or stalls at the video or sometimes works)
    Sw, VLC, and WMP (if it doesn't play the ad)


Video **DOES** work with:
    Sw and VLC (if it plays the ad, otherwise fails right away)
    Sw, VLC and DivX (if it plays the ad)
    Sw, VLC, and QT (maybe 25% of the time)
    Sw, VLC, and WMP (maybe 25% of the time)

It is possible the intermittent success could be improved by changing  the MTU setting.  MTU was set to Automatic for these tests.

It looks like Brightcove is very fragile in some timing or port response. Don't trust it to fly your aircraft or run your heart pacemaker.

---

### Post by pwabrahams on 2013-04-15
Yes, looks like the MTU fix was a false hope.   Brightcove videos are certainly central to the problem, but BBC videos have it also (with a somewhat different error message) and I don't think they use Brightcove.

The oddest thing I observed is that the problem doesn't happen in a newly installed Kubuntu 12.10.  There's something that occurs after the system has been used for a while and updated.

I tried filing an error report with Brightcove but their response was that they don't do Linux.

---

