---
title: "VLC Flicker Issue"
date: 2015-10-12
forum: Multimedia Software
---

### Post by bman on 2015-10-12
Hi,

When ever I maximize or minimize or even just move my mouse VLC flickers either a green square, or green entire screen, within that it seems it might flicker the desktop as well. It is hard to explain.

I am running the latest Nvidia drivers 346 something I believe.

Any ideas?

---

### Post by bman on 2015-10-13
It would seem SMPlayer does not have this issue, but has a few other issues. So I'd like to figure the VLC issue out.

No one has experienced this?

---

### Post by bman on 2015-10-17
So I updated my drivers to the latest 355.11 Nvidia and it seems to have got worse.

Here is a video showing the original issue (green flicker on mouse move, or window changes) and then this distortion of the video on usually window or mouse move.

[https://goo.gl/photos/6tFSNNQUCorHMRBk9](https://goo.gl/photos/6tFSNNQUCorHMRBk9)

---

### Post by QDR06VV9 on 2015-10-17
By your video it appears that you have a laptop? if it is a Optimus  card.
You could try this test ppa mc4man set up to fix most tearing with Optimus cards using nvidia drivers via nvidia-prime.
Instructions, ect. on page
[https://launchpad.net/~mc3man/+archi.../tearfree-test](https://launchpad.net/~mc3man/+archi.../tearfree-test)


To add PPA

```
sudo add-apt-repository ppa:mc3man/tearfree-test
```


Then add the PPA he recomends
```
[FONT=Verdana]sudo add-apt-repository ppa:graphics-drivers/ppa[/FONT]
```


Update && Upgrade your system
```

sudo apt-get update
sudo apt-get upgrade

```

check see if your /etc/X11/xorg.conf Shows this
```
Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
    Option "TearFree" "True"
EndSection
```



To Remove it and revert changes 
```
sudo appt-get install ppa-purge
sudo ppa-purge ppa:mc3man/tearfree-test
sudo apt-get update
sudo apt-get dist-upgrade
```
**If not a Otimus card kindly disregard**

---

### Post by bman on 2015-10-17
Yea no, I have a 980TI in a desktop :)

---

### Post by QDR06VV9 on 2015-10-17
> **bman said:**
> Yea no, I have a 980TI in a desktop :)
Seems you are not the only one.
[https://forums.geforce.com/default/topic/820130/geforce-900-series/gtx-980-tearing-while-watching-youtube-or-vlc/](https://forums.geforce.com/default/topic/820130/geforce-900-series/gtx-980-tearing-while-watching-youtube-or-vlc/)

---

### Post by bman on 2015-10-17
Those seem to be Windows only (which I have no issues with lol) and my issue is only VLC, web stuff is perfect. But thanks.

---

### Post by QDR06VV9 on 2015-10-17
I guess what I was going for is to check Sync to VBlank in Nvidia Settings.
And there were more posts with linux and VLC specific tearing, But I did not post them as there was no solutions.
Out side of that I am all out of Ideas. I would be a bit frustrated at shelling out that kind of $$ for performance like that.
Best Regards

---

### Post by andrew.46 on 2015-10-17
Might be worth a try:

[LIST=1]
[*]Uncheck: Accelerated Video Output (Overlay)
[*]Experiment with the Video Output settings (by default set to 'Automatic')
[*]
[/LIST]

---

### Post by bman on 2015-10-17
> **andrew.46 said:**
> Might be worth a try:

[LIST=1]
[*]Uncheck: Accelerated Video Output (Overlay)
[*]Experiment with the Video Output settings (by default set to 'Automatic')
[*]
[/LIST]

Thanks, yea that was the first thing I tried :)

---

### Post by bman on 2015-10-21
It would seem SMPlayer 15.9 is the best bet. After changing the setting for SMPlayer to use mpv, most problems are gone.

I still have a jaggy/laggy image when moving the actual window around, but not the biggest deal since I don't watch it and move the video around lol

---

