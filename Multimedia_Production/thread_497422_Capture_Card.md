---
title: "Capture Card"
date: 2007-07-10
forum: Multimedia Production
---

### Post by soulraven on 2007-07-10
hy, what capture card, or tv tuner is good and is compatible with ubuntu linux for a live stream?leadtek?avermedia?what?
i need a card with S-Video input and Composite input......

Witch is best and the linux suport is good for my neads.....

sorry for my bead english......

---

### Post by dabl on 2007-07-10
According to the posts I have read, most folks that are getting MythTV to work are using the Hauppauge PCI cards: [http://www.hauppauge.com/pages/prods_pvr.html](http://www.hauppauge.com/pages/prods_pvr.html)

I just ordered a PVR-150 -- I guess we'll see if I can make it work to capture VHS tape. :)

Adaptec had some cards, but they are now discontinued.  I don't know about other ones.

---

### Post by soulraven on 2007-07-10
and is suport for this tuner?the driver is public?or the instalation procedure is complicated and ambigues....

Later edit: i found this page from the ofiicial site: 
[http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page)

i thing this is the best solution......send me a sign when you install the tv card......or anyone?

---

### Post by soulraven on 2007-07-11
this card has anyone tray? work with ubuntu? [http://www.innodv.com/products/smart_capture.html](http://www.innodv.com/products/smart_capture.html)

---

### Post by dabl on 2007-07-11
Hmmm, on their home page, their last "news" was August 2006.  Are you sure they're still there?

Re: Hauppauge PVR-150, the answer to the question "Is the installation procedure complicated and ambiguous?" is in two parts:

(a) the card popped into an empty PCI slot and was recognized correctly by Ubuntu immediately

(b) YES, with regard to installing IVTV -- spent two hours on it last night and got maybe 80% correct.  Got stalled on "copying firmware" -- I may be able to figure it out and finish tonight. [-o<

---

### Post by napsilan on 2007-07-11
I just installed a pchdtv 5500 about a month ago for my mythtv computer, and it works great.  It doesn't have a  hardware analog tv encoder though, but my processor is big enough to handle it.  I don't use the digital/hd portion of it much yet but I figured/hoped that it would be useful in the future (only about 2-3 unencrypted digital channels on my cable).

---

### Post by soulraven on 2007-07-11
> **dabl said:**
> Hmmm, on their home page, their last "news" was August 2006.  Are you sure they're still there?

Re: Hauppauge PVR-150, the answer to the question "Is the installation procedure complicated and ambiguous?" is in two parts:

(a) the card popped into an empty PCI slot and was recognized correctly by Ubuntu immediately

(b) YES, with regard to installing IVTV -- spent two hours on it last night and got maybe 80% correct.  Got stalled on "copying firmware" -- I may be able to figure it out and finish tonight. [-o<

the video input is working?the S-video and composite?you try to make a stream with them?

---

### Post by dabl on 2007-07-11
Nice!

[http://www.pchdtv.com/](http://www.pchdtv.com/)

When I get done recording VHS tapes and get ready to move on to HDTV, this is obviously what I'll want. But I'm not sure how many unencrypted channels I have, if any.  Guess a little research will have to precede the purchase!

Thanks! :)

---

### Post by dabl on 2007-07-11
> **soulraven said:**
> the video input is working?the S-video and composite?you try to make a stream with them?

It "played" a noisy black empty TV screen on my Ubuntu desktop -- it would not show the output of the VCR recorder that was playing the VHS tape. I tried Channel 3 and Channel 4 (on the VCR), I tried the RF cable and the composite video cable, and I "captured" output from /dev/vbi0, /dev/video0, /dev/video24, and /dev/video32, which were the 4 devices that Ubuntu initially assigned it when I rebooted after installing the card. In every case, the "test.mpg" file was empty of video/audio content, so it's not capturing yet.

But, after I installed Mercurial, and the first parts of IVTV, those device settings went away.  I hit a wall installing the firmware when it was required to "unzip" a zip file and unzip apparently isn't in my $PATH.  So, I ran out of time last night, and will have to attack it again tonight, if time permits.  :(

---

### Post by soulraven on 2007-07-11
> **dabl said:**
> It "played" a noisy black empty TV screen on my Ubuntu desktop -- it would not show the output of the VCR recorder that was playing the VHS tape. I tried Channel 3 and Channel 4 (on the VCR), I tried the RF cable and the composite video cable, and I "captured" output from /dev/vbi0, /dev/video0, /dev/video24, and /dev/video32, which were the 4 devices that Ubuntu initially assigned it when I rebooted after installing the card.

But, after I installed Mercurial, and the first parts of IVTV, those device settings went away.  I hit a wall installing the firmware when it was required to "unzip" a zip file and unzip apparently isn't in my $PATH.  So, I ran out of time last night, and will have to attack it again tonight, if time permits.  :(

i hope you finish the instalation OK, because i need help, and i don't know this is the final opion for hardware...the money is limited, because is for a project, Live TV over the internet.....

---

### Post by dabl on 2007-07-11
> **soulraven said:**
> i hope you finish the instalation OK, because i need help

Did you find the README.install file in the IVTV dowload/extracted files?  It is in the /DOCS folder in the extracted files. It gives the detailed instructions that I've been trying to follow.

---

### Post by soulraven on 2007-07-11
in this moment i don't have the capture card......because the buget is verry small, and i want to buy  one time, and work.....

My ID is: YM: soulraventnt
HotMail MSN: tntsoulraven

---

### Post by dabl on 2007-07-11
Ahhh -- OK. Well, the PVR-150 is very cheap.  I'll post if I happen to get it working.   :)

---

### Post by soulraven on 2007-07-11
i hope ......

in the part regarding the software?what server is good?any server suport overlay ? i mean to insert a picture in to the stream......a picture, a date and time, text.......is any software dedicated for this job?

---

### Post by tgm4883 on 2007-07-11
The PVR-150 works out of the box with MythTV and Feisty.  The pcHDTV HD5500 works *almost* out of the box with feisty (you literally have to modprobe 1 driver)

Now i'm not sure why you need the svideo and composite, but it is important what you really plan on using it for as it could change recommendations.  (IE if your hooking up a console vs television, etc)

Regarding the 2 cards above, one is for SD and one is for HD.  (I know the HD5500 does both, but it doesn't have  a hardware encoder for the SD)  So depending on what you want to capture, one card is better than the other.

A third choice if you have a STB is to stream over firewire.  This will give you both SD and HD, but you are still limited to channels that don't have copy protection flags.  In the USA, the law requires that your STB have a functional firewire port.

I have these three things and would recommend the STB over firewire and the PVR-150.  That way you don't have to deal with the crap analog channels over the firewire connection.  There are some flubs in the digital connection every now and then from the cable company that will require a re-priming of the firewire connection, but hopefully this will be fixed with the release of gutsy and MythTV .21

A fourth consideration is the HDHomeRun.  It is about $40 more expensive than the HD5500, but comes with 2 HD tuners, and since it is external and conectable via an ethernet connection, it can be placed anywhere and doesn't take up a pci slot.

@ dabi

I have noticed that the channels I receive with the HD5500 (also applies to the HDHomeRun as they view the same type of channels) are all OTA channels.

---

### Post by soulraven on 2007-07-11
i use Composite and S-video input because the video mixer knows that format...the simple schematics is that.....Video camera-Video mixer-Capture card-Video Server-internet 

thx....
i will buy from my local store from your recomandation PVR-150.....now i have the licente examns and i don't know nothing....

F...k Romania:((

---

### Post by tgm4883 on 2007-07-11
If thats the case, you don't really need a tuner card, as was suggested.

---

### Post by soulraven on 2007-07-11
i know, but i not shure what is good for my configuation...ubuntu...capture card...video stream....

---

### Post by tgm4883 on 2007-07-11
what video mixer is it?

---

### Post by soulraven on 2007-07-11
old one......Panasonic MX20......

---

### Post by tgm4883 on 2007-07-11
I'd go with the PVR 150.  It's a good card and works out of the box.

You don't need mythtv though for this purpose.  You should be able to record directly.

---

### Post by soulraven on 2007-07-11
any server ?what is your recomandation?

---

### Post by dabl on 2007-07-24
I got my PVR-150 working correctly for analog TV capture (out of a VCR, playing a VHS tape).  Here's the basic process:  [http://kubuntuforums.net/forums/index.php?topic=3085164.0](http://kubuntuforums.net/forums/index.php?topic=3085164.0)  :popcorn:

---

### Post by soulraven on 2007-07-26
the PVR-150 has the S-video and the Composite IN?

---

### Post by tgm4883 on 2007-07-26
Yep

---

### Post by dabl on 2007-07-26
> **soulraven said:**
> the PVR-150 has the S-video and the Composite IN?

YEP, but I only got success with the S-Video-IN port, so I had to buy a composite-to-S-Video adapter, and go from Composite-out on the VCR to S-Video in on the PVR-150.  Probably just some dumb goof-up by me, but that's how I made it work.  :)

---

### Post by soulraven on 2007-07-31
have manage some one to stream the sound from a Line In input of a PVR-150? with witch syntax on the command line?with what format?anyone?

---

### Post by hackmeister on 2007-08-01
I'm using the composite inputs on my 150 card in my Myth box. The image (understandably) looks slightly better than the coaxial input.

---

### Post by dabl on 2007-08-01
> **soulraven said:**
> have manage some one to stream the sound from a Line In input of a PVR-150? with witch syntax on the command line?with what format?anyone?

You say "stream" -- I have successfully "recorded" the audio component of a VHS tape, using the S-Video (for video) and the line-in for audio.  I didn't try it in "streaming" or live mode, but I assume it would work that way too.  I used vlc for the recorder/player.   :)

---

