---
title: "Network traffic counter/cell signal display"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by Dedi Landsman on 2009-07-09
I’m considering to move over from windows XP to Ubunntu Linux. At the moment, the only thing which holding me from making the move is that I use cell modem Huawei E169 for Internet on my desktop, I tested it on someone’s Ubuntu, it is well recognized by Ubuntu, but there are two problems remain:
1. I need to have a display of the total kilo/mega/gigabytes downloaded and the possibility to reset/restart the count, [I am subscribed to an internet package with a cellular service provider, limited for a certain Gigabytes per month, over surfing it would mean extra charges]
2.I need to know cell signal reception strength, the way it is displayed in mobile phones [I’m staying at a place with a poor cell signal reception. I’m planning to buy cell repeater to improve that, I need to know the best position for that, to get maximum internet speed].
The above two questions are separating me from moving to Ubuntu Linux. 
Thanks for any help. [Dedi Landsman]("http://ubuntuforums.org/member.php?u=867562")

---

### Post by mtbsoft on 2009-07-22
> **Dedi Landsman said:**
> 1. I need to have a display of the total kilo/mega/gigabytes downloaded and the possibility to reset/restart the count, [I am subscribed to an internet package with a cellular service provider, limited for a certain Gigabytes per month, over surfing it would mean extra charges]
I have a similar modem (E160) which is prepaid and I have to monitor the usage too.  I found a way of integrating vnstat into a conky script using an awk script which shows me my usage on-screen, see [this thread]("http://ubuntuforums.org/showthread.php?t=1193254") for futher info. on that.  If you need any more info. just ask.

As for the speed part, I'm still looking for something to do that myself - my modem (USB) has a blue LED which is dark blue when on HSDPA and light blue when on GPRS but that's all so far.  I haven't found anything yet on how to interrogate the modem after it has connected automatically to get the signal strength.

---

### Post by Dedi Landsman on 2009-07-24
hi, thanks very much for helping. i actually couldn't  hold my curiosity and already installed Ubuntu [wubi] on my desktop. it is up and running, the E169 modem too. because I'm very new to the world of Linux, and has much to learn, the above explanation you gave, is not yet seems to be aplicable to me. meanwhile, by looking up thing on the internet, i found:  [FONT=&quot][[COLOR=blue]http://linux.softpedia.com/get/System/Networking/gtraffic-48737.shtml[/COLOR]]("http://linux.softpedia.com/get/System/Networking/gtraffic-48737.shtml") [/FONT] ,
[http://packages.ubuntu.com/hardy/x11/xfce4-cellmodem-plugin](http://packages.ubuntu.com/hardy/x11/xfce4-cellmodem-plugin)
are these what I'm looking for?
and if so, can they be installed on my wubi?
after i installed Ubuntu i went on to install firewall- Firestarter, generally by following instructions given in "Ubuntu pocket guide and reference", it wasnt exactly the way it goes there, Firestarter wasnt in Synaptic  i had to download it from     [URL="http://www.fs-security.com/"]http://www.fs-security.com/. 
[/URL]
     in the Firestarter Wizard, in selecting the network device/ connection type, there was no "wireless device"option as shown in the abovementioned guide, so i seleccted "dialup device" instead [for my cellular Huawei e169 3G modem which unfotunately,due to poor cell network coverage, most of the time works only on GPRS]. did i made the firestarter configuration OK then? thanks very much for any help.

---

### Post by mtbsoft on 2009-07-27
> **Dedi Landsman said:**
> hi, thanks very much for helping. i actually couldn't  hold my curiosity and already installed Ubuntu [wubi] on my desktop. it is up and running, the E169 modem too. because I'm very new to the world of Linux, and has much to learn, the above explanation you gave, is not yet seems to be aplicable to me. meanwhile, by looking up thing on the internet, i found:  [FONT=&quot][[COLOR=blue]http://linux.softpedia.com/get/System/Networking/gtraffic-48737.shtml[/COLOR]]("http://linux.softpedia.com/get/System/Networking/gtraffic-48737.shtml") [/FONT] ,
[http://packages.ubuntu.com/hardy/x11/xfce4-cellmodem-plugin](http://packages.ubuntu.com/hardy/x11/xfce4-cellmodem-plugin)
are these what I'm looking for?
and if so, can they be installed on my wubi?
Hmm... looks like it should do the trick, though it isn't one I found in my searching.  The advantage of my conky solution is that it is simple there, all the time, painted on the desktop.  However, for a new user, gtraffic looks like a far simpler solution - perhaps you should use this for now and perhaps look at the conky one later if gtraffic doesn't do it for you.  I can't see why it wouldn't work in wubi.

> **Dedi Landsman said:**
> after i installed Ubuntu i went on to install firewall- Firestarter, generally by following instructions given in "Ubuntu pocket guide and reference", it wasnt exactly the way it goes there, Firestarter wasnt in Synaptic  i had to download it from     [URL="http://www.fs-security.com/"]http://www.fs-security.com/. 
[/URL]
     in the Firestarter Wizard, in selecting the network device/ connection type, there was no "wireless device"option as shown in the abovementioned guide, so i seleccted "dialup device" instead [for my cellular Huawei e169 3G modem which unfotunately,due to poor cell network coverage, most of the time works only on GPRS]. did i made the firestarter configuration OK then? thanks very much for any help.
I actually use ufw (Uncomplicated Firewall) - with the gufw interface for configuring it, so I can't offer advice on firestarter.  Again it's down to what you want and how happy you are with configuring the software.  If in doubt, try both and see which you're happier with.

---

### Post by Dedi Landsman on 2009-07-28
Hi, thanks very much for helping. i would like to ask ,please, about the xfce4-cellmodem-plugin, that i mentioned above [that suppose to show cell signal reception strength].
i actualy downloaded it [either with Synaptic or add/remove... i cant remember]. where can i find it in the system and make it up and running [i'm sorry for the question but i'm so new to Ubuntu and Linux].     
thanks for any help

---

### Post by mtbsoft on 2009-07-29
Ok, the panel plugin you mentioned is for xfce4, which is an alternative windowing environment to Gnome (which you are probably using, unless you opted for KDE).  This means you can't plug it in to your existing panels at the bottom and top of your screen.

In order to use the plugin, you will need to install xfce4-panel (it's in synaptic) which is the xfce4 alternative to the panels you have have in Gnome.  Once installed, you can try it out by opening a terminal and typing...
```
xfce4-panel
```
A small panel will appear at the top left of the screen, right click it to add the plugin.  Once everything is configured to your liking, you should add the call to xfce4-panel to your session so that it started at login.

Note, however, that I've tried the above and the plugin seems fairly limited/old and doesn't seem to recognise USB based modems, just "Generic PCMCIA/PCCARD" type modems - I couldn't get it work on mine.

I did find another alternative [here]("http://to2k.com/umts-monitor-for-modem-huawei-e220-in-linux-fedora-8.htm") but it's currently built for Fedora which is RPM based.  I might take a closer look if I get the time.

---

### Post by Dedi Landsman on 2009-07-30
[COLOR=#000000][FONT=Nimbus Roman No9 L, serif][SIZE=4]
[/SIZE][/FONT][/COLOR]
                                                                                                

 [SIZE=3]Hi, thanks very much for helping. I really hope a solution would be found to the problem of displaying cell signal reception strength in Ubuntu. As I mentioned before I'm using cell modem Huawei E169. When working with it in Windows you have a special window that shows [among other things, in a very neat way] the cell signal reception strength; I'm living in a rural area with a poor cell network coverage, inside my home I could, at about 90% of the time, get only GPRS, very rarely UMTS [the modem is capable of an automatic, seamless handover between  GPRS and   UMTS]. The displaying of the signal strength in Windows allowed me to search and find  a suitable spot on the roof [where is maximum reception, any  meter of movement in any direction can make a difference, it is astonishing] to position a special anthena which is connected to the modem, as a result I get now, all the time UMTS. So I hope a solution for that would be found for Ubuntu, without the need to relay on Windows  for that matter,  and some other things like knowing the download speed in Kbps.[/SIZE]
 [SIZE=3]Regarding the application in [/SIZE][[COLOR=#0000ff][FONT=&quot][SIZE=3]http://linux.softpedia.com/get/System/Networking/gtraffic-48737.shtml[/SIZE][/FONT][/COLOR]]("http://linux.softpedia.com/get/System/Networking/gtraffic-48737.shtml")
 [COLOR=#000000][FONT=Nimbus Roman No9 L, serif][SIZE=3]it is mentioned there:[/SIZE][/FONT][/COLOR]
 [COLOR=#008000][FONT=Nimbus Roman No9 L, serif][SIZE=3]**Requirements:**[/SIZE][/FONT][/COLOR][COLOR=#0000ff][FONT=Nimbus Roman No9 L, serif][SIZE=3]

· [gtk+]("http://linux.softpedia.com/get/Programming/Widgets/gtkplus-214-30445.shtml")
· [GConf]("http://linux.softpedia.com/get/Desktop-Environment/Gnome/GConf-4635.shtml")
· [NetworkManager]("http://linux.softpedia.com/get/System/Networking/NetworkManager-6451.shtml")[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Nimbus Roman No9 L, serif][SIZE=3]because I'm so new to Ubuntu,  I don't know if I need to install them, and if so how then, with synaptic? [the gtraffic application is not in synaptic, would it nevertheless be safe to install it?][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Nimbus Roman No9 L, serif][SIZE=3]thanks for any help.  [/SIZE][/FONT][/COLOR]

---

### Post by mtbsoft on 2009-08-03
Is gtraffic safe to install?  Difficult one - personal call, though I likely would as it's distributed on a fairly reputable site.  Most of these have the code available to examine so others would likely have found issues if there were any.  Perhaps do a quick Google to look for references to it, good or bad.

As for the rest of the stuff, usually the installer will identify the dependancies and use aptitude to get anything that is missing but likely as not you'll have those three, they're fairly commonly used.

p.s. Where did you find the antenna, can you remember the site?

---

### Post by Dedi Landsman on 2009-08-05
Hi, thanks very much for helping along. Regarding the the anthena: I didn't find it in the Internet, i got it from my cell service provider company. I don't know its technical name, the web is full of info about this stuff, just click something like: “cellular reception improvement”. The anthena that I have is not a repeater which actually increases and boosts the reception signals, but it is  rather a small anthena, to be placed outside the building and having the principle of bringing the reception that is outside the building to the inside, where it is attached to the modem by a  plastic cleave that is connected to the  wire that connects to the anthena. it is a very small and cheap device, but it did magic to me [it might not work in every case]- enabled me to have all the time UMTS, where before using this anthena I had some 90% of the time GPRS only, which at an everage of about 4 Kbps is extremely slow internet[[]("http://www.google.co.il/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.alternativewireless.com%2Fcellular-antennas%2Fantennaadvice.html&ei=Zs53SquvFMnc-Qat_f2-BQ&usg=AFQjCNFn1XCTddkhpdLjyuMV-Tnhntf24Q&sig2=_6OjfDzJ9GwrjQc1XEFNxA")[[COLOR=#000000]dont[/COLOR]]("http://www.google.co.il/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.alternativewireless.com%2Fcellular-antennas%2Fantennaadvice.html&ei=Zs53SquvFMnc-Qat_f2-BQ&usg=AFQjCNFn1XCTddkhpdLjyuMV-Tnhntf24Q&sig2=_6OjfDzJ9GwrjQc1XEFNxA")[[COLOR=#000000] confuse it with a repeater [/COLOR]]("http://www.google.co.il/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.alternativewireless.com%2Fcellular-antennas%2Fantennaadvice.html&ei=Zs53SquvFMnc-Qat_f2-BQ&usg=AFQjCNFn1XCTddkhpdLjyuMV-Tnhntf24Q&sig2=_6OjfDzJ9GwrjQc1XEFNxA")[[COLOR=#000000]which is[/COLOR]]("http://www.google.co.il/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.alternativewireless.com%2Fcellular-antennas%2Fantennaadvice.html&ei=Zs53SquvFMnc-Qat_f2-BQ&usg=AFQjCNFn1XCTddkhpdLjyuMV-Tnhntf24Q&sig2=_6OjfDzJ9GwrjQc1XEFNxA")[[COLOR=#000000]expensive and connects to electricity, but gives you the advantage of not having to be[/COLOR]]("http://www.google.co.il/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.alternativewireless.com%2Fcellular-antennas%2Fantennaadvice.html&ei=Zs53SquvFMnc-Qat_f2-BQ&usg=AFQjCNFn1XCTddkhpdLjyuMV-Tnhntf24Q&sig2=_6OjfDzJ9GwrjQc1XEFNxA")[COLOR=#000000]connected to a wire inside the house]. The UMTS reception I have now is not its maximum, it's having a download speed  of about 150 kbps, and shows about only 3 bars [out of five], in the cellular signal reception strength indicator at the modem's special window  in Windows[- so badly needed in Ubuntu]. UMTS-HSDPA [“3.5G”] is having the capacity to download at a speed of more than 2 Mbps when signal reception is very strong, so I might buy a repeater beacause it is having the principle also to increase or boost cell signals [ even those “taken” from outside a house], but it may not necessarily work in every case. In the meantime I found this web page [/COLOR][[COLOR=#000000][FONT=Arial][SIZE=2]**gtraffic **[/SIZE][/FONT][/COLOR]]("http://www.gnomefiles.org/app.php/gtraffic")[COLOR=#000000]   in [http://www.gnomefiles.org/app.php/gtraffic](http://www.gnomefiles.org/app.php/gtraffic), which shows the relation of gtraffic to gnome- good news. I still haven't installed the gtraffic application on my Ubuntu: because I'm so new to Ubuntu, i'm learning now some basics of it, and because gtraffic isn't in Synaptic or the Add/ Remove...[how come?] I actually don't know how to install the  gtraffic [having just coming from Windows where i used to install applications by just clicking  icons on the web], if the installation of the gtraffic requires only a few simple steps, please describe them. Thanks very much for any help [/COLOR]

---

### Post by mtbsoft on 2009-08-06
Installing gtraffic is a fairly simple process which the author has summarised as...
```
run sudo ./setup.py install
log out and back in
```

This "translates" to...
download the zip file (it's a tar.gz) and extract to a folder (new?) of your choosing;  
open a terminal window and cd to the folder in question;
type```
sudo ./setup.py install
``` then enter your password when prompted;
once the script has completed, log out then back in, you should now be able to simply type ```
gtraffic
``` in a terminal window to run it.

Not all software goes into synaptic.  I can't say why for sure but new stuff seems to get there eventually - I would guess it has to reach a certain level of development.  It is of course also possible to add other repositories to synaptic to widen your choice - I'll leave you that one to research for homework!!

---

### Post by Dedi Landsman on 2009-08-07
thank you very much for the instructions and help. i have just installed gtraffic, it is up and running and seems to work very well. now i can keep an eye. not to go beyond the 5 Gb download, that I'm subscribed to with the cell service provider company. It is very good that gtraffic has a reset feature- my one month 5Gb. count starts on the 17'th of each month [the day i subscribed], so i can always start neatly there. does vnstat has the reset feature too ?
Hopefully a solution would come to having a cell signal strength display of USB modem in ubuntu. Thanks again.

---

### Post by mtbsoft on 2009-08-08
Now worries, glad to be able to help.  Been there myself, I've only been using Linux for about three years so also still have plenty to learn.

The vnstat method is a bit more complex and I haven't configured it like that yet so it sounds like you have a good solution for you - mine works well for me because it simply paints the values onto the desktop, plus I only need to reset once a year.

---

