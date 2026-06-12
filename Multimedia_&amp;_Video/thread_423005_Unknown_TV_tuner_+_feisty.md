---
title: "Unknown TV tuner + feisty"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by jxd on 2007-04-25
Here's a post for all the adventerous people out there who are going to do what I did today.

I purchased an "Uptech TV7130" card today. It is not listed in the supported tv tuner cards list, but it was based on a supported chipset so I bought it. First problem was figuring out how to make this thing work. 

Feisty is great because the kernel already had everything I needed setup. In fact, the card was automatically loaded when I booted up, just with the wrong parameters. Here is what I did for a saa713x chipset based card:

First, I did "sudo lspci" and made sure the card was there. It showed up as a Philips saa7130 chipset card.

*NOTE these all share the saa7134 driver, even if it's actually a saa7130.

Then, I did "sudo lsmod" and found that saa7134 and saa7134-also were already loaded.

I kept repeating the following loop of steps until I got the card partially working, writing down each card # that worked:

"sudo rmmod saa7134-alsa"
"sudo rmmod saa7134"
"sudo modprobe saa7134 card=<try a card number here>" (I tried everything in the video4linux list)
"tvtime"  

You can use another program to test the tv if you want. To install tvtime, just type "sudo apt-get install tvtime"

I found a few cards worked, but two kept up typing "0" now and then by itself somehow, so I used the only card that didn't have that wierd bug. Now that I knew my card# was 100, I tested every tuner:

"sudo rmmod saa7134-alsa"
"sudo rmmod saa7134"
"sudo modprobe saa7134 card=100 tuner=<try a card number here>" (I tried everything in the video4linux list here too)
"tvtime"  

As for my card, I found my card worked with many tuners, but some of them only went up to channel 51 or so... other tuners could go all the way up to 99+ so I used one of those. They all appeared to be equal quality.

From what I've read online, you're not supposed to get sound in tvtime on your PC, so if you don't have sound don't freak out yet. You have to unmute typing "sudo v4lcfg volume mute off" and then run an application that can handle the sound. Sorry I don't have that information on hand for you.

In my case, I couldn't get the sound working. I believe saa7130 based cards can't get direct sound through the PCI connection (the 7134 can!), that's why they say to hook the line-out from the card to your audio system's line-in, but even the sound output line didn't work for me :( I tried headphones connected directly to it at max volume and still nothing.

POSSIBLE REASON WHY. I live in Taiwan, where all these cards are made, so the box was in Chinese and I can't read 100% yet, but I believe it says "At this time, the TV7130 card is not compatible with computers using the Realtek HD Audio chipset and will result in no sound." My computer uses the Intel HD Audio and I have a feeling it's the same chip... so I am going to return this first thing in the morning and buy a different card.

My configuration on this test PC is Ubuntu Feisty AMD64 running on:
Intel Core2Duo 2.4Ghz 4MB w/ 1Gig DDR2800

Cheers

- JxD

PS Somebody posted a script to test automatically all the cards, I've never tried t though... saw on this website [http://gentoo-wiki.com/HARDWARE_saa7134#v4lctl_Settings]("http://gentoo-wiki.com/HARDWARE_saa7134#v4lctl_Settings") and in case that page disappears, here was the script.

#/bin/sh
MAXTUNER=71
MAXCARD=94
j=0
while [ $j -lt $MAXCARD ];
do
i=0
   while [ $i -lt $MAXTUNER ];
   do
           pccardctl eject  #I use pcmcia card end the card had to be ejected in order to apply new tuner and card numbers. You should delete this line if you use PCI card!
           rmmod tuner saa7134 tda9887
           sync;sync
           sleep 1;
           modprobe saa7134 card=$j tuner=$i
           pccardctl insert #insert card back. You should delete the line if you use PCI card!
           echo "Actual tuner is:" $i "card: " $j
           sleep 1 # this is to make sure /dev/video is registered when tvtime starts

           sync;sync;
           xdtv_scantv -n PAL-I -f pal-europe-west -v4l2 #xdtv_scantv is a fast method of scanning. Change the options to you country. (-n PAL-I -f pal-europe-west works in the UK)
           i=$(($i+1))
   done
   j=$(($j+1))
done

---

### Post by jsym on 2007-04-25
I had a sound issue with Feisty and tvtime as well.  I solved it by opening the volume control and unmuting AUX.  It's a simple suggestion, but it might solve your troubles.

---

### Post by jxd on 2007-04-26
I returned the card and bought the UPMOST MTV instead. It is the exact same card but they replaced  saa7130 with an saa7135 chip. Thus, it now has PCM support, and now warning on the box about the HD Audio incompatibility issue.

I used it with the EXACT SAME CONFIGURATION I had found by trial & error for the other card, since the rest of the hardware looked identical.

TV was up instantly.

I tested the sound with SOX, and success, perfect audio :D

I am using the following script file to load the sound along with TVTIME:

#!/bin/sh
sox -c 2 -r 32000 -t ossdsp /dev/dsp1 -c 2 -r 32000 -t ossdsp /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute

Named it "gotv", placed it in /usr/bin and did a "sudo chmod + x gotv" on it. Voila!

Yay, another new unlisted video card that works perfectly in linux :)

---

