---
title: "Special HomeCinema config .."
date: 2007-10-04
forum: Mythbuntu
---

### Post by Valombre on 2007-10-04
Hello !
My first message around here and a kind of newbie question :biggrin:

Sorry for my english as i'm french, but i'll try to do my best to be understood.

I'm a linux user since 1999, and actually in love with Kubuntu 8)

As i have a pretty good HomeCinema installation 7.1 Infinity Beta Speaker system + Onkyo TX_SR604E AV AmpliTuner, and playing videos with a homeDVD all in YUV cables i would like to upgrade with a all in one box with Mythbuntu.

I found a lot of interesting different hardware but only with Windows software .. definitely not my way !

Of course the choice of hardware is here as usual a problem ..
What i would like in minimum specs :
- video out :YUV  (no HDMI ) dual with vga or DVI ,1080P support
- video in : TV with TNT support
- audio out : optical, digital S/PDIF and standard 3.5 jacks connections
- standard remote  controller (to integrate with my onkyo controller)
- ethernet 10/100/1000
- USB 2 : 2X
- DVD-+RW capabilities
- Small size box, low power consumption (<150 W) external power  would be better (box could be use in a car when traveling)
- Noise at the minimum
- Hard disk : i guess a 2.5 - 160 GO
- remote keyboard/trackball

Example of config but with windows stuff inside =>  the Shuttle XPC 2000 [http://hq1.shuttle.com/products_page03-spec.jsp?PLLI=325&PI=95](http://hq1.shuttle.com/products_page03-spec.jsp?PLLI=325&PI=95)

I guess a good laptop with YUV video and optical-S/PDIF audio could be the solution but i've no clue of finding those kind of laptop config ..](*,)

I hope you could give me some good solutions \\:D/

---

### Post by rusty0101 on 2007-10-06
> **Valombre said:**
> 
I found a lot of interesting different hardware but only with Windows software .. definitely not my way !

If the hardware is set up already some place, ask the people there if you could bring a LiveCD to non-destructively test the hardware to see if it will work for the system you are working on. They are even welcome to disconnect the HD (encouraged actually) as you don't expect to have any need for it.

Take a MythBuntu cd and make sure that it boots and does everything you want with the platform you are looking at. Again, only if the people involved give you the go-ahead.

> **Valombre said:**
> 
Of course the choice of hardware is here as usual a problem ..
What i would like in minimum specs :
- video out :YUV  (no HDMI ) dual with vga or DVI ,1080P support

I'm afraid I'm not much help with this one. yuv may be component out, in which case I know of several video cards with that support, but it's not a given
> **Valombre said:**
> 
- video in : TV with TNT support

I'm not sure what TNT support is to tell the truth. Presumably video capture cards available for your area have this support. I have had good luck with Haupauge! analog cards. 
> **Valombre said:**
> 
- audio out : optical, digital S/PDIF and standard 3.5 jacks connections

I have not done much with optical or coper s/pdif connections.
> **Valombre said:**
> 
- standard remote  controller (to integrate with my onkyo controller)
- ethernet 10/100/1000
- USB 2 : 2X

I would suspect that most of the above (except the video capture) would be available on many good quality mATX motherboards. ITX boards may be available as well. You may have to get 'optional' accessories to support on board s/pdif and IR remotes, but I have seen those features available.
> **Valombre said:**
> 
- DVD-+RW capabilities

They are almost standard hardware at a good computer superstore. I have seen several OEM drives available for under $40(US).
> **Valombre said:**
> 
- Small size box, low power consumption (<150 W) external power  would be better (box could be use in a car when traveling)

Anandtech made a case called the Minuet that I liked very much. mATX format, internal power supply. The restriction being that cards had to be low profile at best.
> **Valombre said:**
> 
- Noise at the minimum

That case did a good job of it. Cooling fans ran on 3v rather than 5v, but I did find that adding a fan to one of them was necessary. 

An ITX board like the VIA with a 1g no fan processor and a mpeg decoder video chip might work well in an itx case with an external power supply. Some of these take laptop hard drives and cd/dvd drives, which may increase costs. I don't know about the audio or ir. An irBlaster may handle the IR input for you, lirc would have to be configured to work with the remote you are interested in using.

> **Valombre said:**
> 
- Hard disk : i guess a 2.5 - 160 GO

2.5 G is on the small side for even the OS for Mythbuntu. Much less capture. mpeg2 video for what we call standard definition in the US runs to about 2.2 gig of content per hour. HDtv that I have been capturing has been a bit over 6 gig per hour. A 160 G drive would give you a bit over 20 hours of hd content unless you transcode to xvid immediately. Obviously a bit more standard definition video. 
> **Valombre said:**
> 
- remote keyboard/trackball

A well configured remote control should give you all the features you're looking for out of a keyboard. Mice (track ball included) don't tend to offer all that much for mythtv, but they are available. I've used a wireless keyboard with an embedded trackpad (not trackball or mouse) that used a usb key to work with the computer. It can be handy while editing or switching to console mode and doing maintenance (apt-get update; apt-get upgrade).

> **Valombre said:**
> 
I guess a good laptop with YUV video and optical-S/PDIF audio could be the solution but i've no clue of finding those kind of laptop config ..](*,)


If you go through the sticky topic, you'll see that at least one person has used a firewire interface to plug into a cable tv box to use it as a tuner. Laptops are about with dvi output, and some of those support a break out cable with yuv connectors. For a worst case situation to get s/pdif out, you could get a pci card with the features on an external adapter, or a usb audio interface with that. I say 'worst case' because both solutions will be rather expensive. A variety of the ITX and mATX motherboards on the market have 5.1 audio out right on the motherboard. It's not as clean as digital, but might be easier to get set up. The usual way of getting that done is to use the mic and line ports for the additional 4 channels. (center, right_rear, left_rear, sub) I would suspect that some laptops will support 5.1 in the same way.

As a start for getting a laptop pre-configured, you might check to see what Dell or Lenovo have in their Linux based laptops. They may have everything you are looking for, or most of it, and you could add what they don't include through after-market adapters (pc-card, usb, etc.)

I've seen some mythtv boxes built with some of the ITX boards sold on ebay. Whether the feature sets include what you are looking for, I don't know.

I won't claim this answers your questions, but hopefully it will get you pointed in a usable direction.

---

### Post by tgm4883 on 2007-10-06
> **rusty0101 said:**
> If the hardware is set up already some place, ask the people there if you could bring a LiveCD to non-destructively test the hardware to see if it will work for the system you are working on. They are even welcome to disconnect the HD (encouraged actually) as you don't expect to have any need for it.

Take a MythBuntu cd and make sure that it boots and does everything you want with the platform you are looking at. Again, only if the people involved give you the go-ahead.


I'm afraid I'm not much help with this one. yuv may be component out, in which case I know of several video cards with that support, but it's not a given

I'm not sure what TNT support is to tell the truth. Presumably video capture cards available for your area have this support. I have had good luck with Haupauge! analog cards. 

I have not done much with optical or coper s/pdif connections.

I would suspect that most of the above (except the video capture) would be available on many good quality mATX motherboards. ITX boards may be available as well. You may have to get 'optional' accessories to support on board s/pdif and IR remotes, but I have seen those features available.

They are almost standard hardware at a good computer superstore. I have seen several OEM drives available for under $40(US).

Anandtech made a case called the Minuet that I liked very much. mATX format, internal power supply. The restriction being that cards had to be low profile at best.

That case did a good job of it. Cooling fans ran on 3v rather than 5v, but I did find that adding a fan to one of them was necessary. 

An ITX board like the VIA with a 1g no fan processor and a mpeg decoder video chip might work well in an itx case with an external power supply. Some of these take laptop hard drives and cd/dvd drives, which may increase costs. I don't know about the audio or ir. An irBlaster may handle the IR input for you, lirc would have to be configured to work with the remote you are interested in using.


2.5 G is on the small side for even the OS for Mythbuntu. Much less capture. mpeg2 video for what we call standard definition in the US runs to about 2.2 gig of content per hour. HDtv that I have been capturing has been a bit over 6 gig per hour. A 160 G drive would give you a bit over 20 hours of hd content unless you transcode to xvid immediately. Obviously a bit more standard definition video. 

A well configured remote control should give you all the features you're looking for out of a keyboard. Mice (track ball included) don't tend to offer all that much for mythtv, but they are available. I've used a wireless keyboard with an embedded trackpad (not trackball or mouse) that used a usb key to work with the computer. It can be handy while editing or switching to console mode and doing maintenance (apt-get update; apt-get upgrade).



If you go through the sticky topic, you'll see that at least one person has used a firewire interface to plug into a cable tv box to use it as a tuner. Laptops are about with dvi output, and some of those support a break out cable with yuv connectors. For a worst case situation to get s/pdif out, you could get a pci card with the features on an external adapter, or a usb audio interface with that. I say 'worst case' because both solutions will be rather expensive. A variety of the ITX and mATX motherboards on the market have 5.1 audio out right on the motherboard. It's not as clean as digital, but might be easier to get set up. The usual way of getting that done is to use the mic and line ports for the additional 4 channels. (center, right_rear, left_rear, sub) I would suspect that some laptops will support 5.1 in the same way.

As a start for getting a laptop pre-configured, you might check to see what Dell or Lenovo have in their Linux based laptops. They may have everything you are looking for, or most of it, and you could add what they don't include through after-market adapters (pc-card, usb, etc.)

I've seen some mythtv boxes built with some of the ITX boards sold on ebay. Whether the feature sets include what you are looking for, I don't know.

I won't claim this answers your questions, but hopefully it will get you pointed in a usable direction.

I think you pretty much nailed a lot of the answers.  I too am not sure about tnt for the video.  Whatever video card he gets needs to support 1920x1080x24p.  The hard drive he was talking about was 2.5in, not GB @ 160GB, which IMO is kinda small for HD recording.  Also, some motherboards have optical and coaxial audio out right on there.  I have one, but it's an atx mb, which sounds too large for what you want.

---

### Post by Valombre on 2007-10-08
Thanks for the answers :)
My first goal using Mythbuntu is to have a all-in-one media box, 24/7 powered because using it like a normal computer (from my couch )+ download + video/audio player, and sometimes TV recorder.
I found a very nice laptop at dell (a XPS [M2010]("http://www.dell.com/content/products/productdetails.aspx/xpsnb_m2010?c=us&cs=19&l=en&s=dhs&~section=specs#tabtop") series) approaching the hardware needed but it's very expensive more than 2999$ .. outch ...  

If somebody has a config near what i want let me know .. most important is YUV outpout and Optical outpout .

---

