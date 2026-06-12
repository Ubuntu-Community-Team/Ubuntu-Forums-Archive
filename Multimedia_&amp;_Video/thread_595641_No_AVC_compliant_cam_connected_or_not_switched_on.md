---
title: "No AV/C compliant cam connected or not switched on?"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by tlie on 2007-10-29
hi,

i have problem using kino video editor, the first time i used it can detect my camera
and capture (though the video image get bad later on)

now, it cannot detect my camera in anyway, even after i modprobe
the raw1394, dv1394 and video1394, etc (using instructions from the net).
[B]
i keep getting message, when i click capture in kino:
"No AV/C compliant cam connected or not switched on?"[/B]

details:
- ubuntu gutsy 7.10
- canon mv960
- VIA firewire VT6306
- kino 1.1.0 

anyone can help? thanks

---

### Post by tlie on 2007-10-30
any multimedia expert can help me?

---

### Post by Amazona aestiva on 2007-10-30
Hi!
First we need to know what broke down, so if you connect the camera to another computer and it recognize it, we'll know that the camera is all right.

Then hmmm I've had a problem like this a week ago. I wasn't able to use Kino for days. I was searching for a solution all the time. Kino couldn't detect my camera till I simply reconnect it.(completely plugged in) Silly a bit... but worked!

If it still doesn't work type: lspci  Terminal'll write down a few devices, where you should see your Firewire port too. If it isn't there, I think... you have to buy a firewire card, or check is it connected well.

And that message means that the port is ready, but no camera found.

---

### Post by tlie on 2007-11-01
tried to connect the canon handycam again after off a few days, but still couldn't detect

lspci also returns a firewire (ieee 1394) device

this firewirecard was working in windows previously in the same PC.
alright, i might stop trying it in ubuntu, maybe after a few weeks i'll try again. thanks

---

### Post by alexisbellido on 2007-12-20
I experienced something like Amazona Aestiva did. My Panasonic PV-GS80 camera, with Trendnet TFW-H3PI Firewire card, wasn't being detected.

At first I followed these instructions to [enable Firewire in Ubuntu Gutsy]("https://help.ubuntu.com/community/Firewire") but Kino didn't detect my camera.

I could see the Firewire card with lspci but Kino didn't detect the camera.

To make sure my Firewire card and camera were ok I went to Winbugs, yeah, even if I didn't like to, and confirmed I had the same problem with Windows Movie Maker.

I opened my PC, removed the Firewire card, started the PC without the Firewire card, then switched off and inserted the Firewire card again. Then I went to Winbugs and now I could see my camera.

Then I went to Ubuntu Gutsy and Kino saw my camera and everything worked ok.

Now, maybe I didn't need removing the card, maybe I just needed to unplug cables and turn off and on the camera, I'm not sure.

I hope this helps others looking to capture video via Firewire with Kino.

---

### Post by Channon on 2008-02-14
Did you find a working solution?  I received the same message (No AV/C compliant cam...?). 

Try hitting the play button the camera itself and see if you get a video stream in the capture window.  I've worked with a lot of capturing programs in XP and found that some do not recognize the camera unless a stream is coming in (let alone allow for control of the camera from the software).  So a crude workaround is to hit the play button on the camera, and then the record button in the software...

---

### Post by tlie on 2008-02-15
i gave up and haven't tried it for a few months. thanks for your info Channon, I'll try your tips one day...

---

### Post by eeclark on 2008-02-22
I entered
```
sudo chmod 777 /dev/raw1394 
```
at the terminal while Kino was running and BAM I got video.
Still had the No AV/C compliant message.
Stopped Kino and restarted Kino
Message gone.

---

