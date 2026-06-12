---
title: "Banshee 2.6.0 drag &amp; drop crash from file manager"
date: 2012-12-06
forum: Multimedia Software
---

### Post by gfunkapus on 2012-12-06
Hi all, I'll start with the pertinent facts and work backwards.

Lubuntu (Ubuntu 12.4.1 LTS) on an IBM ThinkPad X41 with 1.5 GB memory.

It's a fresh install of Lubuntu (3 mos) and Banshee (2 days). It's only used as a audio server (FLACs) to an outboard DAC.

When attempting a drag and drop of a FLAC file from the file manager (PCManFM 0.9.10 LXDE) to Banshee (in any of the accepting locations), the progress bar appears at the bottom left for a moment and then Banshee crashes (disappears).

Poked around /var/log, but haven't found anything relevant. Tried using Thunar file manager with the same result.

I reluctantly moved from Rhythmbox to Banshee, as I was never able to get drag and drop to work with Banshee-- the file would simply not be accepted by Banshee. 
[https://www.youtube.com/watch?v=edoPkSB2Qzg](https://www.youtube.com/watch?v=edoPkSB2Qzg)
With 2.6, it's almost working, but then crashes, as mentioned. 

Googled the heck out of the problem and haven't found any similar situations (besides the YouTube vid). Being I've never had success with Banshee and drag and drop, even when running a full Ubuntu installation on the ThinkPad, I'm starting to wonder if it's hardware related.

Back in the 90's I spent a lot of time with Linux and feel confident to sort this out with some help from some generous soul. 

PS I'm really impressed by the latest version of Lubuntu and all associated Ubuntu software, including Banshee. It's astounding how much it has improved in such a short time. :D

---

### Post by gfunkapus on 2012-12-07
Hi everybody,

After poking around some more, I stumbled on the Apport-Woopsie-Daisy bug reporting tango. It seems Apport was installed, but not the rest. I installed Woopsie, but not clear on whether Daisy is part and parcel. I was hoping it could cache a log that might tell me something.

Anyway, it caught a PCMan file manager crash and seemed to report it. But, when I perform the Banshee drag & drop crash, Apport doesn't seem to notice or report it. Running sudo apport banshee gives this error:
This is not an official Ubuntu package.
Please remove any third party package and try again. 

Since Banshee is an official Ubuntu package, I'm guessing it's complaining about something else.

Anyhoo, I would definitely appreciate any help in my flailing around. Thanks!

---

