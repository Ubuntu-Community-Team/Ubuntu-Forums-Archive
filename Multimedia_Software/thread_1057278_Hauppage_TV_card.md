---
title: "Hauppage TV card"
date: 2009-02-01
forum: Multimedia Software
---

### Post by itsmeok on 2009-02-01
Hello, I have a TV tuner card from Hauppage that I would like to use in linux. I have kubuntu 7.10 running. It is somehow detected but not functioning yet. I found the following thead that shows a list of chips and tuners. I have found the number on my tuner. There are several entries that could be my tuner. I want to try them all as described in the tread:

[http://ubuntuforums.org/showthread.php?t=377290&page=4](http://ubuntuforums.org/showthread.php?t=377290&page=4)

Once you have the tuner chip and the card type unload the current bttv driver and tuner types:

Code:
sudo rmmod bttv
sudo rmmod tuner
Next, load the correct types, substituting the numbers from the lists for x and y:
(Your card was card=10)
(If you have a Phillips NTSC tuner it would be tuner=2)

Code:
sudo modprobe bttv card=X tuner=Y
You may also have luck loading them as 2 separate commands:

Code:
 sudo modprobe bttv card=x
 sudo modprobe tuner type=y

My first question is do I need to restart something after this procedure ?

Second question how could I check that the card actually works. I found the following procedure:

[http://ubuntuforums.org/showthread.php?t=829339&highlight=hauppauge+wintv](http://ubuntuforums.org/showthread.php?t=829339&highlight=hauppauge+wintv)

Now perhaps your device is already working correct. Show us the output of:

Code:
dmesg | grep ivtv
On my computer this looks like:

Code:
dmesg | grep ivtv
ivtv:  Start initialization, version 1.2.1
ivtv0: Initializing card #0
ivtv0: Autodetected Hauppauge card (cx23416 based)
ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
ivtv i2c driver #0: Test OK
ivtv0: Autodetected Hauppauge WinTV PVR-150
ivtv0: Reopen i2c bus for IR-blaster support
cx25840 1-0044: cx25842-24 found @ 0x88 (ivtv i2c driver #0)
tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
ivtv0: Registered device video0 for encoder MPG (4096 kB)
ivtv0: Registered device video32 for encoder YUV (2048 kB)
ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
ivtv0: Registered device video24 for encoder PCM (320 kB)
ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
ivtv:  End initialization
ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
ivtv0: Encoder revision: 0x02060039
As you can see my video device node is video0.
Then you could use cat to test your video device node (if one exists):

Code:
cat /dev/video0 > test.mpeg
This should produce an mpeg video file in you users home directory. Since you did not to tune any channel prior to the cat command you'll only see some flicker in the video file. But in this case your tv-card works.
Now you could proceed to my frontend and use it to watch tv 
In any case you should install tha package "ivtv-utils" via synaptics. If you want to use my frontend there some more dependences.

Third question. 

What is ivtv-utils used for and do i need it if I am going to use myth tv ?

Thanks for all help that you can give.

---

### Post by Macintosh SE on 2009-02-01
ivtv-utils allows you to change channels via command line. I tried to get MythTV working but could not. I tried various other non functioning GUI apps as well. Finally, I gave up and wrote a few shell scripts to view/record TV. I don't know what kind of luck you will have with MythTV, but if you can't get it to work I will post my shell scripts here for you to copy and use.

---

### Post by itsmeok on 2009-02-02
Thanks for your reply and offer. I want to try a bit more. Should I get something back as in the example from the dmesg | grep ivtv command ? Does this proof the card is working ?

And can I change the tuner type as described without restarting the system or something else ?

---

### Post by wolfen69 on 2009-02-02
I have a Hauppauge pvr150 card running on my box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

Media -> Open Capture Device -> PVR (from pull down menu) -> OK
or File>Open Capture Device>PVR Tab>OK if you are using an older version.

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv "remote",(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg

```
it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by itsmeok on 2009-02-03
Hi, now home I have managed to install the software. All the commands are working. I can record something. I am not sure what you mean with VLC player as it is not on my desktop.

Is VLC player installed automatically in kubuntu 7.10 or how do I check if it is installed.

Still the command:

 dmesg | grep ivtv

Does not give anything back as in the example of my first post. Does it give you some info ?

Could I have an issue because I installed my tv card after installing kubuntu ?

---

### Post by wolfen69 on 2009-02-03
vlc is not installed by default.
```
sudo apt-get install vlc
```
if you follow my mini tutorial to the letter, i guarantee it will work.

---

### Post by saedelaere on 2009-02-17
You could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html") to watch TV.

Regards

Saedelaere

---

### Post by cmargolin on 2009-02-17
Here is a useful page: [http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/](http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/)

I use kaffeine with my 950Q on 8.10.

---

### Post by cdnwolf on 2009-02-20
> **cmargolin said:**
> Here is a useful page: [http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/](http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/)

I use kaffeine with my 950Q on 8.10.

I'm having no end of trouble trying to get my 950q up and running on 8.10.

Any chance you could post the steps you took to get yours going?

Thanks

AMD5200+ 64bit Intrepid Ibex

---

### Post by itsmeok on 2009-02-22
I am still trying to get mine to work aswell. Came a bit further because of this thread. 

[http://ubuntuforums.org/showthread.php?t=377290&page=4](http://ubuntuforums.org/showthread.php?t=377290&page=4)

This thread goes about checking if it works.

[http://ubuntuforums.org/showthread.php?t=829339&highlight=hauppauge+wintv](http://ubuntuforums.org/showthread.php?t=829339&highlight=hauppauge+wintv) 

Did you try what wolfen 69 described ?

Success

---

