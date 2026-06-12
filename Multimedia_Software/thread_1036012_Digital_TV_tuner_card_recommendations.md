---
title: "Digital TV tuner card recommendations"
date: 2009-01-10
forum: Multimedia Software
---

### Post by John Jason Jordan on 2009-01-10
I have a desktop computer with Intrepid x86_64. I want to put a TV tuner card into it so I can use it to watch TV. However, I am in the US where analog TV broadcasts will cease on February 17. Therefore, I want a tuner card that can do digital. I have searched everywhere but I cannot find a list of digital cards with Linux drivers and that will work with MythTV and other Linux TV programs. All I can find is that the Hauppauge PVR-150 to PVR-500 line are analog only. Can anyone recommend a digital tuner card or point me to where I can find a list?

---

### Post by wolfen69 on 2009-01-10
> **John Jason Jordan said:**
> All I can find is that the Hauppauge PVR-150 to PVR-500 line are analog only.

i have a pvr-150. that is not true. they will continue to work after feb. 17. it says so on their website.(my signal is digital right now) if you decide to get a pvr, here is a quick start guide you can copy and paste to save time later.

I have a Hauppauge pvr150 (will work for 350 also) card running on my box, and I get tv by:

Code:

```
sudo apt-get install ivtv-utils
```

open VLC player

File -> Open Capture Device -> PVR -> OK or Media>Open Capture Device>select PVR from pull down menu>OK (depending on which version of ubuntu you have.)

then you can do (in terminal)

Code:

```
ivtv-tune -c25
```

(25 is channel number)

which changes the channel.

Code:

```
ivtv-tune -h
```

to see the options which control the card.


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

Code:

```
cat /dev/video0 > /tmp/name_of_file.mpg

```
it will record whatever channel you are on. then ctrl-c to stop.

this has worked for me everytime. have fun.

hope this helps.

---

### Post by John Jason Jordan on 2009-01-10
> **wolfen69 said:**
> i have a pvr-150. that is not true. they will continue to work after feb. 17. it says so on their website.(my signal is digital right now) if you decide to get a pvr, here is a quick start guide you can copy and paste to save time later.

According to Hauppauge the PVR-150 will require a converter box after February 17 unless you have cable television:

[http://www.hauppauge.com/site/products/data_pvr150.html]("http://www.hauppauge.com/site/products/data_pvr150.html")

(You have to click on the Overview tab to see the warning - at the bottom of the page.)

Where did you see that it will continue to work after February 17?

---

### Post by wolfen69 on 2009-01-10
"This Hauppauge WinTV product has only an analog broadcast tuner and will require a converter box after February 17, 2009 **to receive over-the-air broadcasts with an antenna** in the United States because of the transition to digital broadcasting in North America. **Analog only TV receivers [COLOR="Red"]will continue to work as before with cable TV and satellite TV receivers[/COLOR], plus other video devices such as camcorders and VCRs**."

if you get tv via antenna, then yeah, you will need a converter box.

> According to Hauppauge the PVR-150 will require a converter box after February 17 unless you have cable television: 
please re-read the above quote. it will work. is it clear now?

edit: i take it you have an antenna on your roof?

---

### Post by John Jason Jordan on 2009-01-10
> **wolfen69 said:**
> if you get tv via antenna, then yeah, you will need a converter box.

Yes it is clear. I cannot get cable and don't watch TV enough to be worth it to pay for satellite (or cable, for that matter). So I am stuck with broadcast. 

Therefore, as I said at the beginning, I need a **digital** TV tuner card that will work with Linux. I still can't find a list of any TV tuner cards for Linux except the analog cards. Maybe digital cards for Linux don't exist but, if so, at least I'd like to verify it so I can stop googling endlessly.

---

