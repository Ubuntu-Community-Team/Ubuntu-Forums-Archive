---
title: "a thousand paper cuts?"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by namluc on 2009-11-19
A thousand paper cuts pretty much describes my ubuntu experience at the moment. I've been using it for well over a year so am not a noob.

I'm running a hp mini 

First paper cut. wireless

> 
luke@luke-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"TP-LINK_576FC6"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:27:57:6F:C6   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
pan0      no wireless extensions.


i am currently using my neighbours crappy internet. i don't have to. i'm sat next to my router. my computer sees the router but refuses to even try to connect to it.

> 
luke@luke-laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:23:CD:3C:31:1C
                    ESSID:"home"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-33 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:21:27:57:6F:C6
                    ESSID:"TP-LINK_576FC6"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s


my network is the one with the nice name, home. full signal, and completely unencrypted. why will this computer not connect to that network, it is one foot away. my neighbours internet is crap, and has a password, which i have, why does it connect to that one. It will try and connect to any bloody router it can see apart from the one i can see.

papercut 2
 my ethernet has only worked once in the last month, that was last night for an hour.

papercut 3, vlc, xine and songbird

i'm not a music buff but i like to play songs now and then, jaunty was fine, my mac was fine and so was my windows machine, so why is it that whenever i tell vlc or xine to play "this folder" it does so but in a random order. when an album has 12 songs in it, i like to hear them in right order. to get it to do it properly i have to spend 5 minutes telling it song by song what order to play this folder

papercut 4
google earth has not worked on this machine since intrepid

papercut 5
skype keeps changing its settings. i have to fiddle with it for a few minutes every time each time i want to receive or make a call.

papercut 6
the &#8220;expose" function doesn't work after suspend 

1, 2 and 3 are becoming dealbreakers for me, please help me fix them

---

### Post by fluffman86 on 2009-11-19
1. I started noticing the same thing, then I realized by desktop wasn't connecting either.  Is your router dead? Can other computers still connect? Throw in a Karmic LiveCD/USB and test it out.  Connect directly to your modem.  Try a Jaunty liveUSB.

2. Same.

3. Try a music managing program, like Rhythmbox (default) or Banshee (way better).

4. Blame Google.

5. Blame Skype.

6. Blame Compiz, file a bug.

---

### Post by namluc on 2009-11-19
I've been fiddling around with the router, the windows machines can get on my "home" network. This one always always chooses my neighbours over mine!


Both the two networks on the list are both on channel 6, would this cause problems, and why on earth are they both on the same channel?

should my wirless be calling itself eth1, surely that is my ethernets name?

In a fit of frustration i installed karmic on a different partition a week or so ago, the live usb saw my wireless, but when installed, it couldn't see a wireless card at all....

---

### Post by gradinaruvasile on 2009-11-19
Try installing wicd - it is a replacement for metwork-manager. 
First, REINSTALL network-manager - it will download the network manager packages and will have them on the local cache if it is not working out:

In a terminal:

sudo apt-get install --reinstall network-manager network-manager-gnome

Then, install wicd:

sudo apt-get install wicd

reboot is recommended (u can kill nm-applet and launch "wicd-client" by pressing alt+f2 too if u want without reboot)
This will also remove network-manager because it does the same thing. You can reinstall it if you want and dont like wicd by:

sudo apt-get install network-manager

---

### Post by alphaniner on 2009-11-19
> **namluc said:**
> should my wirless be calling itself eth1, surely that is my ethernets name?

Your ethernet is probably eth0.

---

### Post by Giblet5 on 2009-11-19
Having your wifi router on channel 6 - same as the neighbor's - will cause trouble. Maybe not today...but eventually.

Being a foot away from the router can actually make reception worse. RF energy is a fickle beast and will never play by the rules you ascribe to it (it's easy to find dead spots close to any transmitter).

+1 on wicd (does more, better icon, better interface as in not broken like nm-applet, smaller footprint)

Your 'thousand papercuts' is closer to four hair plucks now, right?

---

### Post by namluc on 2009-11-19
I've installed the wicd

automatic connection to my 'home' network, which is great, i like the pop up screen as well. the icon doesn't seem to sit too well with the new karmic look,but i don't care as long as it works!  

ethernet still isn't working as far as i can tell,

and the rest of the papercuts or hair-plucks, will have to wait a few hours...

thanks so far for your help guys

---

### Post by namluc on 2009-11-23
wicd stopped working at random this evening, and refused to connect to a very visible network

sudo apt-get install network manager

and i am back with the default, until this one decides to play silly buggers again, then i suppose i will reinstall wicd...

---

### Post by ccphilly1984 on 2010-02-07
i tried wicd... will not reconnect after i close my netbook lid and reopen it, and if i ioen it after opening the lid, it freezes my whole computer... i really need help to stop this windows type crap from happening... this is the whole reason i got away from windows was system crashing... :(

---

