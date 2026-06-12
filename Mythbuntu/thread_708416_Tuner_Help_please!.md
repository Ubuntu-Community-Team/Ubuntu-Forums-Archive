---
title: "Tuner Help please!"
date: 2008-02-26
forum: Mythbuntu
---

### Post by karlec on 2008-02-26
I have two tuners in my box a PVR-500 and HVR-1800, with a few issues.
[LIST]I am able to watch live TV on one of the tuners in the PVR-500 but when I try to schedule recording at the same time on another channel, I seem to only be recording the "Live TV" show that I am watching.  How do I get second tuner to record on the 500?
[/LIST]
[LIST]
[*]I know that there are no analog support for the HVR-1800, but can someone please help me with a step by step guide on how to get the digital tuner to work (including) how to connect it to my dish box.  I have been reading soooo many guides that I fell that I am loosing it!
[/LIST]

I feel that I am getting close but still need a few things ironed out!!

Thanks.

---

### Post by foxbuntu on 2008-02-28
1) Did you add port video devices from the PVR-500 to your Backend Setup?

2) If you are trying to record HD Content from a US based SAT provider, it can't be done. All HD Content on the SAT baoxes is encrypted and cannot be recorded except with their STB's The only method for recording HD Content at the moment is over-the-air signals for your local broadcast.

---

### Post by elj4176 on 2008-02-28
[QUOTE][2) If you are trying to record HD Content from a US based SAT provider, it can't be done. All HD Content on the SAT baoxes is encrypted and cannot be recorded except with their STB's The only method for recording HD Content at the moment is over-the-air signals for your local broadcast./QUOTE]

Are you saying that if I have Directv and a directv HD box that I cannot put a mythtv box with an HD  tuner between the directv box and my tv and record it? Once it goes through their HD box it should be viewable/recordable by the mythbox right?

Or are you saying that I cannot take the directv signal straight to the mythv box and record it? That's true for the non-HD programming I get now. So I go through their d11-300 box to my mythtv box.

---

### Post by newlinux on 2008-02-28
> **elj4176 said:**
> 
Are you saying that if I have Directv and a directv HD box that I cannot put a mythtv box with an HD  tuner between the directv box and my tv and record it? Once it goes through their HD box it should be viewable/recordable by the mythbox right?

Or are you saying that I cannot take the directv signal straight to the mythv box and record it? That's true for the non-HD programming I get now. So I go through their d11-300 box to my mythtv box.

You can record from the direcTV box via analog capture (s-video or composite), but it won't be in HD. It will be downconverted to SD. In the U.S. your options for HD capture in Myth are:

1. OTA ATSC channels
2. cable unencrypted QAM channels (usually the same ones available via 1.)
3. Firewire capture of non copy protected content from cable set top boxes. What you can get from this method varies from everything to nothing. :)

---

### Post by elj4176 on 2008-02-29
I did some research last night and it seems I will be stuck with a hd-dvr from directv for a little bit (at least on the one TV). I did read on gossamer about a new hd-pvr from hauppauge that is in the works. Maybe that is what I am looking for.

---

### Post by karlec on 2008-03-03
> **foxbuntu said:**
> 1) Did you add port video devices from the PVR-500 to your Backend Setup? 

I am not sure where to do that.

> **foxbuntu said:**
> 2) If you are trying to record HD Content from a US based SAT provider, it can't be done. All HD Content on the SAT baoxes is encrypted and cannot be recorded except with their STB's The only method for recording HD Content at the moment is over-the-air signals for your local broadcast.

I realize that I will not be getting the encrypted channels, but right now I am not getting anything at all out of the card because I don't think that I'm setting it up properly.  So I'm looking for some guidance on how to properly set it up.

Thanks,

---

