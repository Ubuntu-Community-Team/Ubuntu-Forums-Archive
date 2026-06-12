---
title: "Intel GMA 950 - Max Video Ram Possible?"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by redelephant on 2006-09-27
I was given a Dell E1405 with the Intel GMA 950 graphics chip. I've been able to get all of the major stuff running (wifi, correct resolution, etc). But I can't seem to figure out how to increase the memory allocated for the integrated graphics chip. Can anyone here help? If it's of any consequence, dmesg | grep agp shows the following:

[17179588.352000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.388000] agpgart: Detected an Intel 945GM Chipset.
[17179588.388000] agpgart: Detected 7932K stolen memory.
[17179588.404000] agpgart: AGP aperture is 256M @ 0xc0000000

Thanks in advance.

---

### Post by komodojay on 2006-09-27
I am getting one of these tomorrow myself! :D But I believe it is like any other intergrated video card. The Max ram is set in the BIOS not the OS. Try going into that as your Dell Boots.

---

### Post by redelephant on 2006-09-27
I checked the bios, but I couldn't find anywhere to change the video memory. Maybe it's there and I'm just being thick. I'll check again.

---

### Post by komodojay on 2006-09-27
When I get my e1405 tomorrow I'll look it over and see if I can help you out.

---

### Post by redelephant on 2006-09-27
Thanks. I checked the bios again and still no luck. I tried chatting with one of Dell's support people but they were no help either.

---

### Post by odinfromvalhalla on 2006-09-28
i have an intel motherboard with the same Intel GMA 950 and for me it works to change the amount of RAM to use in the BIOS.

---

### Post by manzuk on 2006-09-28
This post is exactly what I was looking for...
Could you tell me how Ubuntu goes on that laptop? (after you get it :D obviously)
I'm considering buying that model (E1405) but I want Ubuntu as my OS, so I really need it to work well with linux.
Thanks and let me know.

---

### Post by redelephant on 2006-09-28
@odinfromvalhalla:
That's what I've done in every other laptop I've owned. But this particular one doesn't seem to have the option in the BIOS. Unless it's there and I just can't find it.

@manzuk:
So far, so good. I've used Ubuntu for years now on various other machines and it hasn't been any harder on this than on others. The only hitch I can think of was dealing with the stupid rescue partition that Dell puts on. Their stuff along with the Windows partition take up three primary partitions. If you just delete it then there's no issue.
I actually like this laptop quite a bit. Mine has a bit of an upgrade in the processor (1.83ghz instead of the stock 1.6ghz), and it's pretty quick. Doesn't seem to run too hot either. The 1440x900 WXGA+ screen looks fantastic once you get the resolution right.

---

### Post by komodojay on 2006-09-30
I just got mine and have most of it set up. I had to do the 915resolution patch to get my screen at 1440x900. [https://help.ubuntu.com/community/i915Driver?highlight=%28915%29]("https://help.ubuntu.com/community/i915Driver?highlight=%28915%29")
In that Wiki in your Xorg.conf file you need to specify how much memory you want the card to use.

Now all I need to do is get the MediaDirect button to launch Amarok instead of Rythmbox.

Hope that helps!

---

