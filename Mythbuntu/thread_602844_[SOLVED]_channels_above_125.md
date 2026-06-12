---
title: "[SOLVED] channels above 125"
date: 2007-11-04
forum: Mythbuntu
---

### Post by supradrvr on 2007-11-04
So  I am back to having a channel issue which I think have found to be a problem with the mythtv frequency selection. I am using Dishnetwork and mythbuntu 7.10. I cant change the channel past 124 because the us-cable only goes that high in the frequency.c file in the mythtv source. So far all I can think to do is add my channels to this file and re-compile. However I cant get it to even get past the configure in mythbuntu. Does any one have a better solution than this? Somebody has to be using mythtv with dish or directv. What are you doing to make yours work? Thanks

---

### Post by supradrvr on 2007-11-04
Ok so I got it to compile without any source code changes. I  had to install a few packages first. build-esential and few dev packages. After successfully getting the compiled from source version working (able to watch tv) I am now re-compiling with a few channels added to the frequency.c file. We will see if it works or not.

---

### Post by supradrvr on 2007-11-04
Ok this procedure worked for me. I edited the file frequencies.c and under the us-cable section I continued to add channel numbers. Then I recompiled and re-installed.I did not need to a frequency for the channel because its sat tv from the composite in.  Here is a samle of the code.

/* US cable */
static struct CHANLIST ntsc_cable[] = {
    { "2",	 55250 },
    { "3",	 61250 },
    { "4",	 67250 },
    { "5",	 77250 },
    { "6",	 83250 },
    { "7",	175250 },
    { "8",	181250 },

.   { "123",	787250 },
    { "124",	793250 },
    { "125",	799250 },
    { "127",           },
    { "128",           },

See where I added 127 and 128. I continued on by adding all my channels from dishnetwork that I needed. This lets the system know that my channels exist now. A little extra work but at least I can change to all my channels now! :)

---

### Post by newlinux on 2007-11-05
Hmm, I don't know if this is at all related, but I use myth from my cable box via firewire and via pvr-150 analaog capture with channels above 125 without any problem. I think I just set the frequency to default. I don't know if this is the same issue...

---

