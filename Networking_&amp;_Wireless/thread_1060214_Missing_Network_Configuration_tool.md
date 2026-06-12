---
title: "Missing Network Configuration tool"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by rabid-gerbil on 2009-02-04
I'm moving from MS Windows to Ubuntu and am having trouble linking to the internet via a Belkin F5D7000 wireless card. I've installed Ubuntu 8.10 onto a PC that is a few years old and have configured it as a dual boot machine. The wireless card works perfectly when using Windows XP Pro so I know the card is OK.

Following a procedure given in WiFiDocs/Driver and elsewhere I located a driver for the wireless card (bcmwl5a) and have installed that using ndiswrapper to reach the stage where using iwconfig indicates the driver is loaded OK.

Both a book I have and the WiFoDocs procedure indicate that I should now configure the wireless network using the menu via a System|Administration|Networking menu item but there is no Networking item in the menu. The nearest I can find is in System|Preferences|Network Configuration where nothing I enter seems to do anything. I've also tried:
   sudo ndisgtk
which opens a Wireless Network Drivers dialog with an entry for the bcmwl5a driver stating that the hardware is present. But when I press the configure button a message is displayed "Could not find a network configuration tool".

I read that configuration via network-admin is possible but typing:    sudo network-admin   in a Terminal window just produces the message "command not found" message.

I've tried reinstalling Ubuntu in case something I did somehow lost the configuration tool but that is no better.

How do I get over the hurdle of this missing tool, is there anything I should download and install? Bear in mind that the Ubuntu machine has no internet connection so anything I download has to be via another PC and USB memory stick transfer. Also I am completely new to Ubuntu and Linux so please keep any instructions simple>

Many thanks

---

### Post by monikersupreme on 2009-02-10
Not that it helps much but I'm in the same boat as you, I've checked the ndiswrapper sticky as well but to no avail. 

I am trying to install drivers for a Trendnet TEW-643pi PCI wireless-N card and am running v8.10 (ignore my sig, I'm using different hardware) dual booting with XP however if I can't get the network card working I may very well just blow away Ubuntu and run solely on XP w/ Cygwin (not my preference but if I don't have reliable connectivity there isn't much point.

---

### Post by rabid-gerbil on 2009-02-11
Thanks for your reply.

Yes I nearly gave up with Ubuntu particularly as I have had no reply in this forum (until yours of course).

I got round the problem by downloading Ubuntu 8.4 which does have a Network configuration tool. But my first attempts to configure the wireless card didn't work and I've yet to try again. Instead for now I've installed Ubuntu 8.4 on another PC (dual booted) with an Ethernet link to my wireless router and, running Ubuntu, it connected with the outside world beautifully with no problems at all. So I'm working with that for now and will return to the other PC when I'm more experienced with Ubuntu.

---

### Post by Corniger on 2009-02-18
I also have the same problem. The installation **seems** incomplete. But after a total of about 6 hours of searching I found something on a **Weather Stations Forum** :p

> If you cant find an icon for network manager (should be on the top bar to the right) you can alwys open a console window and type -

sudo nm-applet 


In the meanwhile I'm not even sure anymore what that applet really is - if it is the little crossed out Network icon that you click on to see the wireless networks you can click on, but not connect to, it's there.

But what's the "could not find network configuration tool" then... I can (unless I follow the install procedures with ndiswrapper) see and click on networks but I never get a connection.

Also the WPA pwd I type in always ends up as a huge array of numbers and letters, like it was encrypted or so. I experienced stuff like that in windows before and when I re-entered the pwd it would work, but no chance here with "out of the box" - I have no idea what else to do. I cannot complete any tutorial of the "just works" installation, because there's stuff MISSING - or "missing".

That finally, after being on the lowest point of using computers since 20 years leads to the following conclusion:

On Ubuntugeeks I saw some "Anti-Elitists" bitching about the "Elitists" destroying Linux by not being able to "get BASIC THINGS straight" - so I really don't know anymore whether it's my incompetence with Linux or networking or someting else. I really wanna get on with what I was actually planning to do with Ubuntu: work. 

Right now all i can feel is sheer frustration. Wherever you look, read, ask BEFORE you install you see "it just WORKS. No more fiddling around with driver CDs". Well, for the past 2 1/2 days all I did was fiddle around - but not with driver CDs (I'd LOVE to have some stupid driver CDs now!!!), but with what I basically left behind with Windows 3.11, or before XP Service Pack 2 with Windows firewall when I still had to remove viruses manually in DOS with a boot floppy disk.

I really don't mind working on command line and stuff, but all that bragging on how easy it is and how well it works (my soundcard doesn't work, my Wlan doesn't work and I wonder if I'll manage to install the NVidia driver, that I also can't just click on, or even run from command line) now seems a LITTLE exaggerated to me. I really wouldn't mind if somebody had said "it can be tricky and might take a few days/weeks", but all I was told is "piece of cake" and so on. And I don't seem to be alone.

> Everything you need comes on one CD, providing a complete working environment. Additional software is available online.

Except if the network configuration tool is missing and you can't get online...

> The graphical installer enables you to get up and running quickly and easily. A standard installation should take less than 25 minutes.

I'm close to 25 hours now and nowhere near up and running.

> Once installed your system is immediately ready-to-use. On the desktop you have a full set of productivity, internet, drawing and graphics applications, and games.

That is definitely correct. Aside from sound, 3d graphics and wlan. But the software definitely rocks, no bitching there.

> On the server you get just what you need to get up and running and nothing you don't. 

In case you can get online to access that server :p

Furthermore I had the sound configuration utility and the VPN configuration utility crash several times. Good ol' Windows feeling.

What I definitely DO like: it comes, as said, with all sorts of cool Open Source software, preinstalled, always up to date, free to use and developed faster than anything. I definitely love the community idea, and with Blender it has helped me tremendously. It looks good, it feels good, I LIKE IT and I WOULD LIKE TO USE IT!

But guys, a little more honesty! I think what Open Source does is the best thing in the world that happens NOWHERE else, in no other aspect of life. So of course, there needs to be some pride about that. My highest regards to the programmers who make this happen, I always totally sucked at programming and I admire people who contribute to such great things FOR FREE. I get help FOR FREE to use something that is FREE. I don't get any help at all from an incompetent Antivirus company that costs me 50 bucks a year.

Example:
It's hard to learn Blender, the UI is weird and you really have to bite your way through it, but _nobody ever said Blender was easy_! **Why is it that Ubuntu doesn't simply admit that?** I'm sure there are thousands of people without problems, but I really must say that the only problems I remember having had with Windows were compatibility issues of hardware products with each other, especially for audio engineering, and bad software that didn't have anything to do with Windows itself. And that the WG111v2 also seems to suck on Windows - or is it my board's USB dropping out? I'll never know.

**So please "sell" it as what it is, not what people would like it to be. It's FREE, so whoever wants to bitch then should shut it and LEARN it.** 
I'm bitching because I was basically "tricked" into something I would have thought twice about doing during a week of holidays! Sorry! ;) Maybe I'm just really out of luck right now, but that seems kind of improbable looking at the issues and the solutions that obviously aren't available.

---

### Post by rabid-gerbil on 2009-02-18
Well that's 3 of us who have experienced this problem. ](*,)

See my reply to the other poster to see what I am doing. I think I'll stick with Ubuntu 8.4 for now as that will have long term support.

Your frustration has been much greater than mine. What surprises me is that no one has has posted a solution to what is (or should be) a trivial problem. It looks as if there are so many questions asked in this forum so our problem just got lost in the flood.

It's sad if newbies get frustrated and put off Ubuntu just because simple questions like this don't get answered.

---

### Post by Flymo on 2009-02-18
Well, folks, at least I know   _-why-_   my own nm-applet is missing.....
I removed the wrong darn thing from my panel!  :oops:

Ubuntu 804 on an Acer 4315, Celeron 540, intel 810 graphics
and Atheros WiFi using NDISwrapper, no problems with it until I did the deed.

I tried ```
sudo nm-applet --sm-disable
```

...which does nothing that I can see, putting it in the background with '&' does the same...

[URL="http://www.linuxquestions.org/questions/linux-newbie-8/no-more-wireless-connection-in-mn-applet-ubuntu-7.10-598769/"]
Found this at Linux-questions which helped me.[/URL]

The relevant part there for me was :-
```
Check to see if nm-applet is a running (or sleeping)process. If so try this:
In the panel (toolbar) right click
- add to panel
- Notification area icon (scroll down under utilities

```
...then added the Notification Area to the panel - Success!

Found that I had indeed started three instances of nm-applet, but I knew that already from trying ```
ps -ef | grep nm-applet
``` in the terminal.

If your problems are deeper-seated, and WiFi driver related, then this will not be much help, but it might be confusing the issue, so it is worth checking.

Had to struggle with WiFi initially, but no problems (at least none that I did not make for myself) recently.  NDISwrapper solved the problem on this machine, and Simon Bridge got all the bugs out of 804 using MadWiFi for the wireless and documented it [here]("http://www.hbclinux.net.nz/acer4315.html").

Now that 810 is out, it seems as though all the problems with the Acer 4315 have gone, which is not a lot of help to you.  All the while that my nm-applet display was missing, the WiFi was working fine.

Hope that something here was useful to you.

All the best, Ben

---

### Post by Gramps on 2009-02-18
> **rabid-gerbil said:**
> I'm moving from MS Windows to Ubuntu and am having trouble linking to the internet via a Belkin F5D7000 wireless card. I've installed Ubuntu 8.10 onto a PC that is a few years old and have configured it as a dual boot machine. The wireless card works perfectly when using Windows XP Pro so I know the card is OK.

[This might help....]("http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide")

---

### Post by Corniger on 2009-02-19
> **Gramps said:**
> [This might help....]("http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide")

> This should enable you to see and configure your wireless card in System->Administration->Networking

There **is** no menu item called "Networking"!

I did NOT remove anything, not even unknowingly. I've had 3 810 installs now. No "Networking".

---

### Post by Corniger on 2009-02-19
> **rabid-gerbil said:**
> Well that's 3 of us who have experienced this problem. ](*,)

See my reply to the other poster to see what I am doing. I think I'll stick with Ubuntu 8.4 for now as that will have long term support.
I saw many more on other forums. Unfortunately the solutions are always for older Ubuntu versions or simply can't be performed, because the "network config tool" and the menu item "Networking" JUST AREN'T THERE.
I can't follow that support thing. You get an "old" version that is being supported for a longer period of time than the new one? What does that mean? 

> Your frustration has been much greater than mine. What surprises me is that no one has has posted a solution to what is (or should be) a trivial problem. It looks as if there are so many questions asked in this forum so our problem just got lost in the flood.

Yes, I can understand that though, look at the stats - there are up to 25.000 people on here at the same time and our problem sure is a minor one. Still - up to 25.000 could mean about 100 that could help.
> 
It's sad if newbies get frustrated and put off Ubuntu just because simple questions like this don't get answered.

I'm not sure this is something people in the forum CAN actually really help. If something just isn't there, it's not there, or the piece of software, that says it's not there, is too old to recognize it's there. This is a developer thing, and within the 3 days I've found a lot of help, just all of it is useless, because the installation seems incomplete. I know, I'd probably just have to get online to OK I'M STOPPING IT NOW :P

I got [one more solution]("http://ubuntuforums.org/showpost.php?p=6758603&postcount=4") on another post of mine. I'll try this afternoon (luckily I'll be home before 21:00) and then step down to 804, cause it seems I'm not only wasting my personal time, but also other people's time with intrepid. Missing Network configuration tool, missing Networking menu item... that spooks me and I don't wanna invest much more time
for something that seems unfinished. That's why I never switched to Vista - and now I experience everything in Ubuntu Inrepid that I wanted to avoid :P So maybe going back to 804 ("XP") is a better idea.

---

### Post by Corniger on 2009-02-19
Oh, btw: the "Missing Network item" issue doesn't seem to be new. There was a [whole thread]("http://ubuntuforums.org/showpost.php?p=5376804&postcount=1") concerning it. It popped up **ONLY 7 months ago** and was assigned "high priority". Thread closed.

So I'm definitely going to ditch 810 and try 804. That's no fun. Really. I mean, I didn't pay for anything, accomplish/contribute anything and it's free and all, and I don't know anything about Linux so I suck, but this is kind of ridiculous :roll:

It's kind of strange this didn't occur to anybody since then. There must be thousands of intrepid users by now, and this didn't pop up any question marks?? Probably because their wireless works...

---

### Post by Corniger on 2009-02-19
OK, also no chance with the compat-wireless tool. Great. I just installed 810 for the 5th time and see if compat does anything now. I already downloaded 804 and then that will be my last try.

---

### Post by rabid-gerbil on 2009-02-22
> **Gramps said:**
> [This might help....]("http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide")

Well it might if there was a menu item called Networking actually existing under System->Administration. But it ain't there.

---

### Post by rabid-gerbil on 2009-02-22
> **Corniger said:**
> I saw many more on other forums. Unfortunately the solutions are always for older Ubuntu versions or simply can't be performed, because the "network config tool" and the menu item "Networking" JUST AREN'T THERE.
I can't follow that support thing. You get an "old" version that is being supported for a longer period of time than the new one? What does that mean? 

I believe that it means they are committed to supporting 8.04 for 2 or 3 years for organisations who don't want the (potential) hassle of switching to a new version every 6 months. Organisations like stability - so do I

> **Corniger said:**
> That's why I never switched to Vista - and now I experience everything in Ubuntu Inrepid that I wanted to avoid :P So maybe going back to 804 ("XP") is a better idea.

8.04 has been fine for me since I reverted to it. I've not tried going back to getting the wireless card going on the other machine yet - I've too much else to do.

Good luck

---

### Post by rabid-gerbil on 2009-02-22
> **Flymo said:**
> Well, folks, at least I know   _-why-_   my own nm-applet is missing.....
I removed the wrong darn thing from my panel!  :oops:

Ubuntu 804 on an Acer 4315, Celeron 540, intel 810 graphics
and Atheros WiFi using NDISwrapper, no problems with it until I did the deed.

I tried ```
sudo nm-applet --sm-disable
```

...which does nothing that I can see, putting it in the background with '&' does the same...

[URL="http://www.linuxquestions.org/questions/linux-newbie-8/no-more-wireless-connection-in-mn-applet-ubuntu-7.10-598769/"]
Found this at Linux-questions which helped me.[/URL]

The relevant part there for me was :-
```
Check to see if nm-applet is a running (or sleeping)process. If so try this:
In the panel (toolbar) right click
- add to panel
- Notification area icon (scroll down under utilities

```
...then added the Notification Area to the panel - Success!

Found that I had indeed started three instances of nm-applet, but I knew that already from trying ```
ps -ef | grep nm-applet
``` in the terminal.

If your problems are deeper-seated, and WiFi driver related, then this will not be much help, but it might be confusing the issue, so it is worth checking.

Had to struggle with WiFi initially, but no problems (at least none that I did not make for myself) recently.  NDISwrapper solved the problem on this machine, and Simon Bridge got all the bugs out of 804 using MadWiFi for the wireless and documented it [here]("http://www.hbclinux.net.nz/acer4315.html").

Now that 810 is out, it seems as though all the problems with the Acer 4315 have gone, which is not a lot of help to you.  All the while that my nm-applet display was missing, the WiFi was working fine.

Hope that something here was useful to you.

All the best, Ben

Thanks for the info, I'll see how it goes when I can face tackling the wireless card again.

---

### Post by Corniger on 2009-02-22
> **rabid-gerbil said:**
> Well it might if there was a menu item called Networking actually existing under System->Administration. But it ain't there.

That's because there is none in 810. After one week of useless research someone happened to tell me this. So forget all the guides, they're outdated and won't work. I'm also no longer sure what the problem really is. There's network. There's the device, yet no connection and noone seems to know how it's supposed to work. Back to XP, back to working, bye to fiddling.

---

### Post by Corniger on 2009-02-22
> **rabid-gerbil said:**
> Thanks for the info, I'll see how it goes when I can face tackling the wireless card again.

Feel lucky? Get a new wireless, and maybe also a new router ;-) Or an OS...

---

### Post by rabid-gerbil on 2009-02-25
> **Corniger said:**
> That's because there is none in 810. After one week of useless research someone happened to tell me this. So forget all the guides, they're outdated and won't work. I'm also no longer sure what the problem really is. There's network. There's the device, yet no connection and noone seems to know how it's supposed to work. Back to XP, back to working, bye to fiddling.

So how are new users supposed to know what to do, is wireless network configuration meant to happen automagically? It's a shame if you give up on Ububtu. Ubuntu will never enter the bulk market if it isn't easy to get things like wireless cards running without a lot of fiddling. I've just spotted the following in the 8.10 release notes, I've no idea if it will help but I'll try it sometime:

[QUOTE=8.10 Release Notes]Only US wireless channels enabled by default on Intel 3945

The iwl3945 wireless driver defaults to the US regulatory domain for wireless, so wireless networks on channels forbidden by US regulations but permitted by European or Japanese regulations will not work out of the box. This affects IEEE 802.11b/g channels 12 (Europe and Japan), 13 (Europe and Japan), and 14 (Japan only), as well as all 802.11a channels. (Some other wireless drivers may be affected; this is the only one we are sure of so far.)

To work around this, add the following line to the /etc/modprobe.d/options file if you use this driver and need to use European wireless channels:

options cfg80211 ieee80211_regdom=EU

Alternatively, add the following line if you use this driver and need to use Japanese wireless channels:

options cfg80211 ieee80211_regdom=JP[/QUOTE]

---

### Post by Corniger on 2009-02-25
It seems to work for many people, and I would LOVE to use it. I almost had gotten used to the UI already and it kind of stung to go back to XP. But I have my peace back. 

But the amount of frustration, plus the amount of outdated or ultra-complicated guides are simply just too much for me. Or guys closing threads when finally someone was about to help you because expressing yourself while going almost crazy isn't Ubuntu enough. 
Maybe I'll try version 10.x again ;)

---

