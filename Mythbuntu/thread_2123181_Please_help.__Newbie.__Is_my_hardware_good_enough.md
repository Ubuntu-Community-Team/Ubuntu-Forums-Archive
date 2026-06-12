---
title: "Please help.  Newbie.  Is my hardware good enough?"
date: 2013-03-07
forum: Mythbuntu
---

### Post by iboothy on 2013-03-07
I am converting an old HP Pavilion t3255.uk to run Mythtv as a FE and BE. I don't need to run any live TV, just as a media player for now. I will look to build a new machine when I need to run Freesat.
Will this spec work? I have successfully installed Ubuntu as a test and it seems to work well.
Sorry if these questions are stupid, but I'm new to all this.
Also I will be upgrading the graphics card to give me HDMI. I was looking at a GeForce 610, 620 or 630. Any advantages or disadvantages to any of these?

Here is the spec of the PC...  [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00543258&lang=en&cc=us&taskId=101&prodSeriesId=1148603&prodTypeId=12454](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00543258&lang=en&cc=us&taskId=101&prodSeriesId=1148603&prodTypeId=12454)

---

### Post by PhilWig on 2013-03-09
A few personal views:

Does it do (and will you want to exploit) wake-up so you can run it like a video recorder rather than a 24/7 server?  Look up ACPI wakeup in the wiki.
 
Are there enough slots on the mobo for your display and capture cards?

Live tv is no different to record and playback.

1Gb is low - add 2 X 512Mb or preferably 2 X 1Gb and you'll never swap.  

You'll probably want to add a second big disk for recordings - 2Tb say - within 5 months.  At that stage split operating system (including database) plus swap on one, media on the other.  Use spare space on the smaller disk for resilience.

2.8GHz CPU is fine - especially if you have proper hardware assist from capture and graphics cards. 

See this thread for info on graphics cards.  You are wise to avoid ATI.
[http://ubuntuforums.org/showthread.php?t=2118107](http://ubuntuforums.org/showthread.php?t=2118107)

The question you didn't ask was about capture card.   You mention satellite but please do check compatibility before you buy.

Phil

---

### Post by cbennett a7xftw on 2013-03-09
Yeah, you'll be fine. Just don't do anything too strenuous, and upgrade the RAM if you can.

---

### Post by aormond on 2013-03-10
I love MythTV, but in my opinion if you're not interested in video capture you're better off going with XBMC. It's a lot less fussy.

---

### Post by iboothy on 2013-03-11
Thanks for the messages.
Mythbuntu ran fine and the machine is not slow at all.  As this is only for a media server I guessed I would not need anything too powerful.
The only problem I've run into is running audio through the HDMI.  The problem is that there is no audio.  I installed a GeForce graphics card which works fine for picture output, but no audio is heard at all.  The motherboard has onboard sound so I don't know if this is affecting things.  Any help would be appreciated.

---

### Post by PhilWig on 2013-03-11
Try this:
[http://www.mythtvtalk.com/hdmi-audio-sound-mythbuntu-how-configure-ubuntu-hdmi-audio-16043/](http://www.mythtvtalk.com/hdmi-audio-sound-mythbuntu-how-configure-ubuntu-hdmi-audio-16043/)
Regards
Phil

---

### Post by iboothy on 2013-03-12
Thanks PhilWig, I will take a look tonight when I get home from work.
I've read a few posts and most people seem to have installed MythTV onto Ubuntu, whereas I have just installed Mythbuntu.  I'm starting to think that I might be better to install it on to Ubuntu.  Are there any advantages/disadvantages to either method?

---

### Post by PhilWig on 2013-03-12
You'll get lots of differing views on this.  I use Mythbuntu as well which I find nice and stable - 12.04 was a doddle to set up.
If it's working apart from the one issue of sound I'd stick as you'd probably get that problem on Ubuntu + mythtv anyway.
Phil

---

### Post by iboothy on 2013-03-12
If I can't solve the problem then my only option is to buy separate speakers, but I don't really want to do that.
My biggest issue is I'm used to Windows and solving the sound problem would be quite easy.  Since I am new to Linux, it's all so unfarmiliar and I don't know where to start.  I keep reading about ALSA, which I have an idea of what it is.  But whether I have or where I find it is another matter.

---

### Post by iboothy on 2013-03-12
PhilWig.  I owe you a virtual beer!!!
Got my sound working thanks to your link above.  I will paste below the solution.
My next task is to get Mythmote to connect but I've been unsuccessful so far.  If you've got any tips I would be grateful.

Here is the sound solution...

[COLOR=#ff0000][I][B]Try this:
1. Ensure you have no VGA devices connected. They can inhibit HDMI.
2. Very important: update Nvidia driver. Hint: Control Centre > graphics driver > restricted drivers > [recommended] driver
3. In frontend, get audio config in setup>Audio:
Alter device until test gives hissing noise.
On my system it's 
ALSA:dmix:CARD=NVidea,DEV=3
4. If still not working try alsamixer in a terminal session. Change volume settings then repeat step 3.
5. If working in myth but not in browser or mythnetvision, see [/B][/I][/COLOR]*[COLOR=#ff0000][/COLOR]*

---

### Post by PhilWig on 2013-03-13
In case anyone else hits this, in retrospect, I should have said:
step 1:  If you do unplug VGA then do a cold boot (some capture cards seem to need this)
Did you need to run Alsamixer in step 4?  If so, then steps 3 & 4 should have been swapped.


I've not run mythmote but do you have the addresses right?
a) a fixed IP address for your backend.  I use DHCP but the router gives same fixed address each time.
b) set that address in backend setup (twice).
c) you can leave frontend setting at localhost or 127.0.0.1
Phil

---

### Post by zero-g on 2013-03-13
Hi iboothy, just wanted to know what version of Ubuntu you're using and what Nvidia card you ended up with? A friend of mine has an Nvidia 630 and it's giving him grief, I'm not sure it's the card though.

---

### Post by PhilWig on 2013-03-13
I'm a bit apprehensive about the way that this thread is becoming  forum of its own and propose we close it.
Separate threads for hardware suitability, sound, mythmote and nVidea cards would have been more useful, but I plead guilty to being main culprit! 
Phil

---

### Post by iboothy on 2013-03-13
Hi,
After a bit of searching I think the MythMote problem is due to the fact that MythTV is listening to localhost.  Apparently it should be listening to all local network.
Can anyone explain in layman's terms how I go about achieving this?

---

### Post by iboothy on 2013-03-13
Ooops,
Didn't realise there was a page 2.  Sorry.
Also, apologies for lack of forum etiquette.
Zero-G: Mythbuntu 12.04 and NVIDIA GeForce 630.

---

