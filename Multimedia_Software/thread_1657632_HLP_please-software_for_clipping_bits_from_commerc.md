---
title: "HLP please-software for clipping bits from commercial DVDs?"
date: 2011-01-01
forum: Multimedia Software
---

### Post by dooper on 2011-01-01
Hello,i run Ubuntu lucid lynx and am looking to pinch bits from commercial DVDs to use for example as youtube uploads or for editing.

Am i looking for a ripper or transcoder?

I have looked at the included software but none of it seems to work!

Thanks

---

### Post by oldos2er on 2011-01-01
I think you could do this with vlc's record function.

---

### Post by oldos2er on 2011-01-01
[deleted]

---

### Post by dooper on 2011-01-01
Further to my OP,i have now upgraded to the latest Maverick Meerkat as i read that Handbrake was highly recommended for what i am looking to do.

Having visited the Handbrake website..I am at a loss as to how to download the software.

I expects a clickable link>download>install but I'm not seeing anything like that and it appears to want ne to register???

---

### Post by JohnAStebbins on 2011-01-02
> **dooper said:**
> Further to my OP,i have now upgraded to the latest Maverick Meerkat as i read that Handbrake was highly recommended for what i am looking to do.

Having visited the Handbrake website..I am at a loss as to how to download the software.

I expects a clickable link>download>install but I'm not seeing anything like that and it appears to want ne to register???
The last official release of HandBrake doesn't run on recent versions of ubuntu, so direct links to the old package were removed and replaced by a link to the nightly builds which takes you here
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

If you follow the instructions on that page, you can install the PPA as a software source so that the ubuntu package manager can install and update HandBrake from the PPA.

Short answer, run this in a terminal:
```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
sudo apt-get install handbrake-cli

```

---

### Post by dooper on 2011-01-02
Thanks John..

Ran the terminal commands and now have the GUI version installed so will have a play!

Thanks

Joe

EDIT..software works ok but apparently disk is encrypted etc etc so not readable.

---

### Post by BicyclerBoy on 2011-01-02
You need to search for restricted formats dvd playback on the Ubuntu website.

This will instruct you to install libdvdread libdvdnav libdvdcss etc..

In addition to HandBrake, DVDRip & ffmpeg & AVIDemux could do what you want but with a big learning curve..

---

