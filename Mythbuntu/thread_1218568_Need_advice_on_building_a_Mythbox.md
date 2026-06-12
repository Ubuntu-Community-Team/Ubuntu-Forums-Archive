---
title: "Need advice on building a Mythbox"
date: 2009-07-20
forum: Mythbuntu
---

### Post by deamon_knight on 2009-07-20
I'm looking to move from an old XPMCE system to building a new MythTV syste, but I'm looking for some advice. I have a system that could be rebuilt for a myth TV box. Here are the specs.

CPU: AMD Athlon 7850
MB: Abit NF-M2S Nvidia 6100 Chipset
2GB RAM
500GB HDD
Soundcard: Soundblaster Audigy 2.

Remote is USB WinMCE IR Remote.

Any reason this hardware might not work?

I think I'll need to buy a new vidcard. Suggestions are to get an Nvidia 7series or higher for VPAUD. I have a Hauppage PVR-150, and I think I may add a Hauppage HVR-1600 and 1800.

I'd like to know if there is a reason to buy a video card with HDMI, my Display has either HDMI or VGA, whats the benefit of getting HDMI, or is it more trouble than it is worth?

I'm really interested in the Multirec feature, but I'm not clear if this is only for ClearQAM in North America or if it can be used with OvertheAir ATSC Broadcasts as well.

Is there any easy way to find out if my cable provider offers channels in ClearQAM? (Time Warner Cable,Columbus,Ohio)

Any other hurdles I should watch out for?

Thanks

---

### Post by chipppy on 2009-07-21
Good Evening

I am in Aussie so I cannot help with the American channels part.

As to the hardware.  It looks good in general
With HDMI you only really need it if you TV needs it.  Personaly I run my HTPC on a 12 year old Standard 68cm Cathrode Ray Tube (CRT) via a composite cable.  This keep everyone in the house happy, especially the kids (mostly old cartoons).  
The one downside of low definition picture is if I am doing any terminal work I need to connect up a LCD monitor so I can read the smaller text.  But I dont really do that much terminal work anymore so all is good.

If you have the high definition TV, great, and you need the high definition connections, if not, also great, go for the low definition connection and enjoy.

Cheers
chipppy

---

### Post by newlinux on 2009-07-21
If you want to use VDPAU most 7 series won't do. Check [http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards) for compatible cards. If you are only going to be playing ATSC OTA content (which is mpeg-2) you CPU is more than enough, and you don't need VDPAU, but it will certainly offload a ton of the processing onto your vid card. Your Hauppage PVR-150 won't produce any recordings that will come close to taxing your CPU or needing VDPAU.

Multi-rec works with ATSC OTA content. Just remember to record two different channels at once with one tuner the channels need to be on the same multiplex.


As for what stations are offered in clear QAM, that varies greatly from region to region, even with the same provider (what comcast offers in clearQAM one place could be different in another place). A couple of ways to check:

1. Go to avsforum and find the forum for users who have your local subscriber. They probably keep track there.

2. Your location and provider may be in the database: [http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

---

### Post by deamon_knight on 2009-07-21
Thanks Guys, that helps alot. My TV is a 42" LCD, it has a VGA and an HDMI, and my MCE box is connected via VGA. The question is if HDMI would be better in some way, or if is needed at all. I understand that it is more of a hassle to set up piping SPDIF audio to the vidcard and out through HDMI. Correct me if I'm wrong, but do you NEED HDMI for any reason? BluRay? Any HiDef Contant? I don't Imagine I'll encounter too many problems with HDCP on Linux but I wanted to ask.

Basically that leaves two possible HD sources, ATSC OTA and ClearQAM from the cable provider. Newlinux's link shows broadcasts in both (Assumming QAM256 is clearQAM), but how can I determine how many multiplexes that is? If I spring for two digital Tuners, say an HVR-1600&1800, I'll have 2 analog for Cable, one digital for cable and one digital for OTA. 

I thought that OTA was "true" HiDef, while cable was not full 1080p, so OTA would be preferable where possible, or am I way off base?

Ultimately, the objective here is to to to identify hardware that will "Just work" before I buy. But will CPU/MoBo play a big role in making/breaking a Mythbuntu Install? Looks like Capture cards and vidcards, and possibly soundcards especially in the case of HDMI, are what you need to pay the most attention to.

---

### Post by utar on 2009-07-22
I personally use a DVI to HDMI converter and separate audio inputs to connect my Myth box to my TV which works great.  There is a noticeable difference between the box being connected via analogue VGA and the digital HDMI sockets so I would definitely go for a HDMI connection.

Some people have problems with HDMI audio, although I believe most issues can be fixed.

There is no *need* for HDMI on Linux as HDCP isn't supported and blu-rays, for example, can only be played if the discs are decrypted and the video files ripped.



Utar

---

### Post by newlinux on 2009-07-22
ATSC OTA is not really what you are calling true HD (1080p) because no channels broadcast 1080p. All the HDATSC OTA channels broadcast 720p or 1080i and it will be captured in mpeg-2. Also, not all ATSC OTA channels are HD. Some are SD (like the subchannels).

From the HDHomerun listing, you can tell if the are on the same multiplex if the number before the hyphen in the channel column is the same. e.g. if Channel A is 79-1 and channel B is 79-3 they are on the same multiplex, and can be recorded at the same time on one tuner.

The only benefit HDMI has over DVI-D in Linux has is the ability to run audio with the signal. I use DVI-D -> HDMI cords too on a couple of my sets. Now whether or not there is an advantage of HDMI over VGA is in picture quality depends on a lot of factors, the biggest of which is your TV set. On a couple of the HDTVs I've had the picture is indistinguishable, on others, it has been very noticeable - using the same hardware. I had a computer connected to a westinghouse HDTV and the picture was indistinguishable between VGA and HDMI (after tuning the picture with Digital video essentials). That set crapped out on me and I bought a Samsung HDTV set and the HDMI quality was very noticeable better than the VGA input. So it depends...


Also most TV sets by default overscan the HDMI input, but don't overscan the VGA output. Some sets allow you to turn off the overscan in HDMI, others don't except in the service menu. And some sets allow a different level of control of picture settings on the HDMI input than they do on the VGA input, including what resolutions each input accepts.


CPU is important in that it needs to be powerful enough (in combination with whatever GPU you buy). The mobo just needs to be supported in Linux. Tuner and vid card are the most important. Stick with nvidia, and if I was being new I'd get one with VDPAU capabilities. But for the content you are looking to play (mpeg-2 HD), the onboard nvidia 6100 is sufficient with that processer. If you check my hardware in the link in my sig, you can see what I use to playback HD.

---

### Post by deamon_knight on 2009-07-22
Thanks again newlinux, thats all a big help. I think the Overscan with HDMI was where my problem lay. I don't think I'll spend the $$ on a vidcard with HDMI yet. Any suggestions on a digital tuner card? The HVR-1600 or 1800 look like the way to go, although its a shame the 2200 or whatever the Hauppauge to one is called, isn't well supported, 2 Digital and 2 Analog tuners on one card with one coax input, I'm worried about loss of signal quality with all the splitter I'd need. Even a modest pair of 1600s will have four inputs, even dedicating one of the digital inputs for OTA you still have to split three ways, and two more if I were to add the PVR-150s. Still, 2 digital 4 analog tuners is alot of TV.

---

### Post by newlinux on 2009-07-22
sorry, I haven't bought a digital tuner in over 2 years. The old PCI ones I bought years ago aren't available anymore. I assume you are looking for a PCIe card. My suggestion is to look into a couple and then google and check these forums for how hard they are to get working. You might also want to consider the HD homerun.

In one of my machines I have 3 tuners, and a coax running into my TV, using a 4 way splitter (I do have it amplified). Works great. All depends on the signal you have coming in. I have two other machines that have the signal split 2 ways, not amplified.

---

