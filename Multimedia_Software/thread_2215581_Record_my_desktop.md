---
title: "Record my desktop"
date: 2014-04-07
forum: Multimedia Software
---

### Post by alfirdaous on 2014-04-07
Hello everybody,

I would like to record my desktop while doing some explanation, which tool is the best to do so?

Thx in advance

---

### Post by slickymaster on 2014-04-07
[recordMyDesktop]("http://recordmydesktop.sourceforge.net/about.php")
[SimpleScreenRecorder]("http://www.maartenbaert.be/simplescreenrecorder/")

---

### Post by alfirdaous on 2014-04-07
Thanks [**[COLOR=#C61919][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126"), is there one that highlight the mouse (like yellow color) and we can explain on the screen (something like a pencil)?

---

### Post by slickymaster on 2014-04-07
Not sure, but you can take a look at [this]("http://recordmydesktop.sourceforge.net/rug/p1_3d.php") and check if that's what you're after.

---

### Post by 23dornot23d on 2014-04-07
sudo apt-get install vokoscreen

vokoscreen ........ 

and using cairo-dock .... there is a addon to highlight the mouse pointer ....

also if you are doing it in Gnome-shell I think the mouse pointer can be set to show up in gnome-tweak-tools.

There may be better ways to do this - but one thing with vokoscreen is it works properly even when compiz is running 

which you will find recordmydesktop starts to tear diagonally across the screen with that ....... 

like if you have got compiz running - unity is a compiz addon -  recordmydesktop might cause problems in it.

as for the mouse highlighting - same as above - cairo dock - Gnome-shell have ways to highlight it - maybe it works in Unity
too - but not tried it.

---

### Post by monkeybrain20122 on 2014-04-07
kazam is by far the best, you can also record sound (from system output and/or voice over) It is in the repo for Ubuntu 13.10, ppa for 12.04. Unfortunately it doesn't highlight the mouse (not that I know of, may be there is a setting..) If you have slow cpu you may need to decrease the fps in the settings.

It works perfectly on Unity, but appears to be broken on gnome shell (on Fedora, but then it may be Fedora or a my compilation, need to compile in Fedora). 

I see recordmydesktop is often recommended but in my experience it is garbage, it is buggy and doesn't work with composting and 3d desktops.

---

### Post by alfirdaous on 2014-04-08
@[**[COLOR=#C61919][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126"): eventhough I checked follow mouse curosor in advanced options, it does NOT change anything

[**[COLOR=#000000]@23dornot23d[/COLOR]**]("http://ubuntuforums.org/member.php?u=953253"): I installed vokoscreen as well as cairo-dock, BUT how to use it to highlight the mouse pointer?
@[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403"): kazam does NOT have a mouse hilighter

---

### Post by slickymaster on 2014-04-08
> **alfirdaous said:**
> @[**[COLOR=#C61919][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126"): eventhough I checked follow mouse curosor in advanced options, it does NOT change anything
<...snip...>

I am sorry but I'm not able to help you there since I've never used any of these applications. But if you'll be patient I'm sure that someone here in the forums will come up with a solution for you.

---

### Post by monkeybrain20122 on 2014-04-08
> **alfirdaous said:**
> 
@[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403"): kazam does NOT have a mouse hilighter

There may be some workarounds [https://bugs.launchpad.net/kazam/+bug/655602](https://bugs.launchpad.net/kazam/+bug/655602)

---

### Post by 23dornot23d on 2014-04-08
There is a video here that explains how to use vokoscreen for screencasting ...... [http://youtu.be/R23RyFvXDG0](http://youtu.be/R23RyFvXDG0)

The highlighting of the mouse in cairo may not be sufficient for what you require - as when it is on - it only highlights
things within cairo's own areas created on the screen ........ and is more of a gimmick fun thing than for presentations .....
flames around the cursor may not be what you are looking for here .........

I also was using gnome-shell ...... within the latest gnome-tweak-tool there is a option to show the mouse .... 
and a blue animated pulse circle appears around where the mouse is when used with the ctrl key I think !!!
Ubuntu - 14.04 was what I tested this in though ........

What desktop are you doing this screencast in .......

Is vokoscreen not sufficient to create one with ..... 

( I will look for more information on the vokoscreen site and ask if they have plans for a highlight mouse mode )

sudo apt-get install keymon

keymon

May be what you now need to complete this .......

If you want to visualize the mouse , the "keymon" tool may help you.
[http://iloveubuntu.net/keymon-handy-mouse-and-keyboard-visual-monitor](http://iloveubuntu.net/keymon-handy-mouse-and-keyboard-visual-monitor)

This is from this link .... [http://www.kohaupt-online.de/hp/](http://www.kohaupt-online.de/hp/)

It is a german site - but by pressing the uk flag near the top of the page - each page is then changed to English.

I just did a quick video to try it out ...... here ....... [http://youtu.be/4juLJdooZAI](http://youtu.be/4juLJdooZAI)

There may be a lot more to this .... as I just had a quick glance and installed and ran it ...... 

so its not a brilliant demo ....... and no sound only because I do not like my own voice recordings.

I will see if I can do one in Gnome-Shell as there new highlighting method was showing up much better
( I maybe need to do some google searches to find how far this is has progressed )

---

### Post by alfirdaous on 2014-04-08
I think compiz has these functionalities,  tried to install and run it, but it seems does NOT work, I am using Ubuntu 12.10
[http://askubuntu.com/questions/328543/drawing-over-the-desktop](http://askubuntu.com/questions/328543/drawing-over-the-desktop)

---

### Post by 23dornot23d on 2014-04-08
I see what you want now .... not just to highlight the mouse ........ but to draw on the screen with it like a whiteboard.

I have it running in one version of compiz ..... in 12.04 ......

Let me see if I can find something else with that sort of functionality .

[http://www.ubuntuvibes.com/2011/02/ardesia-07-released-brings-interactive.html](http://www.ubuntuvibes.com/2011/02/ardesia-07-released-brings-interactive.html)

[B]its still in the repository .... and although old .... might still work on the right desktop .........

sudo apt-get install ardesia[/B]


Here is an old video of it - but it still works ...... [http://youtu.be/4Wd8SsmIjzs](http://youtu.be/4Wd8SsmIjzs)

I will post a video - I have done shortly with it ....... Done .....( [http://youtu.be/yUTPHYw7pmo](http://youtu.be/yUTPHYw7pmo) )



[SIZE=1]*or we search on compiz and see if its a bug and there has been a fix for it ........... if it is a bug in 12.10 .........*[/SIZE]

---

### Post by alfirdaous on 2014-04-08
I used Ardesia, it is nice, but I can get to run compiz, it has more functionality, does it works with Ubuntu 13? so I can upgrade and let it run

---

### Post by 23dornot23d on 2014-04-08
If you cannot run compositing - then the chances are that none of the whiteboard applications will work as they
sit on a transparent layer from what I am seeing ..........

> 
I used Ardesia, it is nice, 

but I can get to run compiz, it has more  functionality, does it works with Ubuntu 13? 

so I can upgrade and let it  run


Not sure I fully understand - ( You can or cannot run compiz at the moment ? ) 

we best find out what you have running first.

What graphics card do you have in your computer ....... what sort of computer are we using here. laptop / desktop

There are other things for drawing on screen ....... but not overlay - but if you do not need overlay then I can

search and see what else is available ...... what sort of diagrams or sketching on screen are you doing ...... ?

Did you see the videos that I posted .... are you sure compiz annotate has more functionality .... as I did not see it.

I ran Ardesia in the latest version of Ubuntu 14.04 .. and it still runs - just have to drag the overlay around so it does not
cover the menu up ...

---

### Post by alfirdaous on 2014-04-09
> **23dornot23d said:**
> If you cannot run compositing - then the chances are that none of the whiteboard applications will work as they
sit on a transparent layer from what I am seeing ..........
Not sure I fully understand - ( You can or cannot run compiz at the moment ? ) 


I can open the compiz but to have as 3D and use its functionalities, I cannot.

> What graphics card do you have in your computer ....... what sort of computer are we using here. laptop / desktop

I am using NVIDIA in HP Laptop

```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```


> search and see what else is available ...... what sort of diagrams or sketching on screen are you doing ...... ?

I would like only to explain things, such as highlighting words, underline,... simple things

>  Did you see the videos that I posted .... are you sure compiz annotate has more functionality .... as I did not see it.

Yes, I used kazam for a few seconds, and the result is almost 1.2 GB

---

### Post by 23dornot23d on 2014-04-09
Have you got Nvidia-settings installed and working and what graphics drivers are you using for it .........

Maybe its a case of getting it working better ..... so that compiz works ..... and then you should be sorted.

But remembering back the 8400M GS was a problem card to setup.

If you have Nvidia-settings working - can you see what driver is running please ........

it will look something like this if its working ...... 

[IMG]http://markbrewster.files.wordpress.com/2010/02/screenshot-nvidia-x-server-settings.png?w=500&h=286[/IMG]

Just a thought as that may be the only reason you cannot quite get what you want yet.

Its an old card though ...... and the later drivers do not seem to be as good as the
earlier ones for these older cards. ( or nouveau takes over )

Best I can think of for now .... but it may be a way forward - unless you have already tried
things and not got anywhere with them ...... seems a few reports about the 8400M GS on
the web ....... but all relating to very old OS's.

---

### Post by alfirdaous on 2014-04-15
how can I get NVIDIA settings?

---

