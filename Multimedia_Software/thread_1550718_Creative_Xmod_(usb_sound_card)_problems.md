---
title: "Creative Xmod (usb sound card) problems"
date: 2010-08-11
forum: Multimedia Software
---

### Post by BinoPanda on 2010-08-11
Hi, I've been using ubuntu for years but have never needed to post any problems because usually I just search the forums and somebody has a fix. In this case I'd looked through the forums and found numerous threads regarding the Xmod but many of them rely on something called "asoundconf" which does not seem to function in newer releases of ubuntu. What I'm looking for help with is getting my Xmod to output sould for the entire system. 

   By default the volume knob on the Xmod changes my master volume but at any level nothing plays. The only instance where I can get sound to come from my xmod is when I go into the Multimedia Systems Selector, set my default output to ALSA and and my device as USB Audio. After setting this I click the test button, the test beep is played and the knob adjusts the volume. Aside from that the Xmod makes no sound, I know the device works though because I've used it on my windows box.

thankyou in advance for any responses ^_^

Bino

---

### Post by BinoPanda on 2010-08-12
bump 

:(

---

### Post by BinoPanda on 2010-08-18
bump

---

### Post by aytchforrest on 2010-08-19
bump. having the same problem on lucid, which I installed yesterday (had been using Windows for a while... now Flash, Mendeley, and assorted codecs are the only closed source software on my whole machine but... my headphone jack has been broken for a while (unreliable as headphones don't fit right and are scratchy, and built in speakers are frequently just "off" due to registering headphones as present when they're not) and an effective solution had been to use my Creative XMod to listen to audio. Now on Ubuntu, it doesn't work:

1) Only registers as supporting input in various system and program mixers after plugged in
2) If computer boots with it in, or I run pulseaudio -k in the terminal, mixers recognize several outputs... none of which do anything whatsoever.
3) Volume knob DOES work to control computer volume...
4) The input that can be enabled doesn't actually work.

---

### Post by aytchforrest on 2010-08-24
I've got my XMod working fairly well now.

I followed both sets of modifications to the default.conf file mentioned in this thread:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/429642](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/429642)

However, by default the XMod is set to a volume of 0 in the ALSA mixer when first plugged in, or upon things like reboot. I bound the following command (in my case, to Ctrl+my mute function-key) in Compiz, since I generally use that for a lot of my custom hotkeys, but you could access it however is convenient for you:

amixer -c<Card#> cset numid=<ID> <some value>

You'll need to change the values in the brackets:
<Card#> depends on how many cards you have. I only have the onboard one plus the XMod so I just use "-c1" for this part. You can find this simply by running alsamixer in shell, and pressing F6 to switch soundcards. There will be an index number to the left of the XMod.

The ID for my XMod output was 5, so "cset numid=5". You can find this by running "amixer -c<yourCard#> controls" which will show all the possible control indexes. 

Finally the actual volume. It seems to be a percentage scale from 1-100, but the number you use with amixer isn't exactly what you see in the alsamixer graphical gauge or the percentage of the volume. In fact it's about half, though not quite. I don't really feel like trying a whole lot of values right now but 30 gives me 63 in alsamixer, and 39 gives me 77. This part you can just mess with and find a volume that you like.

I tried to get this to just happen as a triggered udev rule but I couldn't get it to work very well... could be a fairly good solution if someone reading this is more familiar with shell scripting and input device rules.

Anyway this works as a stopgap and the card is very usable. However I am still trying to find some way to force the XMod's volume control to control the XMod volume - then the problem of having the XMod be muted by default won't even require a hotkey. Not sure how to do that yet and I've only been running Ubuntu for about a week now, so any help with inputs and such is appreciated!

---

