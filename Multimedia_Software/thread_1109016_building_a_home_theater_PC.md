---
title: "building a home theater PC"
date: 2009-03-28
forum: Multimedia Software
---

### Post by rainsideways on 2009-03-28
Basically, I want a way to plug my various digital media files into my standard home theater system. I don't intend to use this system to decode HD signals or do TV tuning, so I don't think the hardware needs to be all that powerful, though it obviously needs to be new enough to support the HDMI out. If I can use standard Ubuntu, that would be stellar, though I am not totally opposed to trying something like mythbuntu that has been designed more for media needs (though I don't think I need something like mythtv since I don't plan on using this as a DVR).

My priorities are:

- Video and audio supported over HDMI
- Only two cables: power and HDMI (so wireless network)
- Small form factor
- Cheap

Based on the web browsing that I have done so far, it looks like Nvidia is the way to go, and that recent drivers should be able to support HDMI (including the bundled audio). I don't intend to stream my data files over the network, so network lag should not be a concern; I plan to scp them to the box so they are playing off local hard disk. Support for an IR remote might be nice, but is not critical (I figure I can control the system remotely with a laptop on the same wireless network).

I think I want to go mini-ITX form factor. Can anyone recommend some hardware that they have had good experiences with? The more that is integrated on the motherboard the better. I am very comfortable with Linux troubleshooting, though I have not been following hardware releases very closely.

Any other suggestions welcome. :-) Thanks in advance.

---

### Post by jt_04 on 2009-03-28
I just finished building my htpc.  I think another priority you should have is noise level.  Here is what I used in my PC:

Antec NSK2480 MicroATX case ([newegg link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811129034"), [silent PC link]("http://www.silentpcreview.com/article591-page1.html"))
ASUS M3N78-EM Motherboard ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131354"))
AMD Athlon 64 X2 5200 Brisbane 2.7GHz 65 Watts ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103210"))
SILVERSTONE NT07-AM2 80mm CPU Cooler ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835220030&Tpk=NT07-AM2"))
MSI N9400GT-MD512H GeForce 9400 GT ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127396"))
EDIMAX EW-7128G PCI Wireless Card ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041"))
LG Black Blu-ray/HD DVD-ROM GGC-H20L ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827136133"))
4GB Corsair DDR2 800 RAM
Hauppage WinTV-HVR-1600

When I first built it up, the noise was deafening.  The first video card I bought had a fan, which was very loud, and the stock CPU fan was very loud.  Combined, it was too loud for my living room.  so I returned the video card and got the passively cooled card listed above.  and I bought the CPU cooler listed above.  These two upgrades, combined with the very quiet NSK2480 case, made my PC whisper quiet.  You can barely hear in running in a quiet room, and with the TV on, you can't hear it at all.  

another thing that helped me get whisper quiet was the 65 watt CPU.  much easier to cool than a 125 Watt cpu.  in fact, the CPU cooler listed above is only good for < 65 watts.

Because of the difficulties with Blu-ray on Linux, my plan was to install WinXP and Ubuntu, and just boot into windows when I wanted to watch a blu-ray.  So I installed WinXP first, and everything worked great.  I have great video and audio over the HDMI connection through the video card to my Sony Bravia 40" 1080p TV.  I had an overscan issue at first but the updated nvidia 9400 drivers fixed it by letting me rescale my video output.  

The blu-ray drive and bundled software (PowerDVD 7.3) works great for older blu-rays, but is incapable of playing new blu-rays because of the outdated AACS encryption keys that came with it.  I am still talking with Cyberlink support over email about this to get my AACS keys updated and so far they have been incompetent but decent responsiveness and helpfulness.

Next I installed Ubuntu and got it working fine, except for the video.  I have tried every Nvidia driver out there, even the beta 185 version, but Ubuntu will only run in low-graphics mode.  It gives some error about "No usable screens found".  It doesn't know what kind of monitor is attached.  I am thinking it is something to do with the HDMI connection and my next attempt to fix it will be to use a VGA connection.

By the way, that cheap wireless card I listed above works great in Ubuntu and Windows.  My speeds are not that impressive but I can easily watch TV episodes off the internet without it choking.  

All told, with my 640GB hard drive, this system cost me $680 to build.  I got several components, including the case, on sale, so I saved almost $200 from retail prices.

---

### Post by littlehonda on 2009-03-28
JT, I basically have the identical setup as you (less the dual booting) and similar problems:
[http://www.avsforum.com/avs-vb/showthread.php?t=1132383]("http://www.avsforum.com/avs-vb/showthread.php?t=1132383")

It will take a bit of work, but having ditched Windoze, I am going to give it my best shot to make it work.  Keep in touch and please post updates ...

LH

---

### Post by lovinglinux on 2009-03-28
Since you don't need a PVR or stream media to other machines, then Mythbuntu is overkill. You could use [XBMC]("http://xbmc.org/").

---

### Post by jt_04 on 2009-03-29
> **littlehonda said:**
> JT, I basically have the identical setup as you (less the dual booting) and similar problems:
[http://www.avsforum.com/avs-vb/showthread.php?t=1132383]("http://www.avsforum.com/avs-vb/showthread.php?t=1132383")

It will take a bit of work, but having ditched Windoze, I am going to give it my best shot to make it work.  Keep in touch and please post updates ...

LH

wow, thanks...it's nice to know that i'm not the only one struggling here.

I've been working on it off and on and I think the problem stems from my computer not recognizing the EDID info from my TV, so it doesn't know what modes it can display (hence the "no usable configuration found" error).  i found out what edid is [by reading here]("http://www.avsforum.com/avs-vb/archive/index.php/t-803681.html").

 i confirmed this by following the instructions [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760") (installing the read-edid and xresprobe pkgs and using those commands (get-edid and ddcprobe) both failed in reading the edid info from the tv).

I did all that over VGA too, and it still couldn't read the edid.  

i think my next step is to connect my spare 15" LCD monitor and make sure that works, to make sure the edid problem is on the TV end, not the PC end.  

and I also want to do some more research into the right modelines for my TV ([read here]("http://www.mythtv.org/wiki/Modeline_Database")).  it seems that if you know the modelines for your tv, you can specify them in your xorg.conf file and just force it (?).  my TV model isn't listed on that page, so I briefly tried a similar one with no luck, but I want to try it again over VGA.  maybe you can find your TV model in that database and give it a shot?

not sure if I'm on the right path with all this, so let me know what you find on your end.

jt

---

### Post by medicis on 2009-05-02
I hope you all don't mind a relative noob ask a related question.

my system:
Gigabyte EP45-UD3R
Intel Dual Core 2.5 GHZ (not overclocked)
MSI N9400GT-MD512H GeForce 9400 GT
EDIMAX EW-7128G PCI Wireless Card
ACER 24
4GB DDR2 800 RAM
pcHDTV 5500
Full duplex 6 chan sound card

When I first installed the new motherboard, CPU, and Video card (the TV and sound cards were already in place), and 9,04 Ubuntu had been installed a few days before. I made the mistake of compounding my probs due to the introduction of new unknowns ... the hardware upgrade plus 9.04. 

The first thing I found was that of the various computer 'hangs' I experienced, many were resolved by replacing the 9400GT with my prior card, a NVIDIA 6600. Like some here, I had upgraded to the 9400GT to obtain HDMI output. 

However, with my graphics working (with the 6600) I was able to resolve many of the software issues that were causing 'hangs' so that everything was pretty stable using the 6600Gt. I downloaded the correct driver from NVIDIA using EnvyNG which installed it. (haven't verified that yet because I'm just learning the command line commands). But when I installed the 8400GT the 'Hangs' returned. Occurring at various times but all within a very few minutes. 

Anyway, I thought I'd post this problem because of the common prob with the 9400GT. If I find any solutions elsewhere I'll post them here for reference regarding 9400GT/NVIDIA issues.

---

### Post by jrice219 on 2009-05-02
Basically, I built a HTPC out of an old emachine and an old video card laying around. I would use XBMC as my program of choice. Boxee is another option but Boxee is a fork from XBMC. Boxee is more "social" oriented. XBMC is great. You can stream from your network (optional), play basically any video format (with codecs installed), and even install scripts. Like TV shack, ANIMESEED, and there is a hulu script being assembled (from the last time I checked).

---

