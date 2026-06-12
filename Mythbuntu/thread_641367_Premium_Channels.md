---
title: "Premium Channels"
date: 2007-12-15
forum: Mythbuntu
---

### Post by tj71587 on 2007-12-15
Which Tuner cards would support channels above 100, like HBO and other channels in the 500's?

---

### Post by spalVl on 2007-12-15
It really depends.  In the US (not sure about abroad)

Most Cable Companies have moved the premium channels to STB only.  So the days of capturing HBO with an analog tuner without STB are pretty much gone as a whole YMMV depending on location and provider.  I have Comcast   

Standard Def- 

STB s-video to s-video input -  Most cards like PVR-x50 support this.  The added headache is  also setting up an IRblaster or serial channel changer to have the STB channel changed.  Basically any card that works with Linux and MythTV will work for this.  Many shapes and sizes of IRblaster some models of PVR 150 have built in IRblaster.

High Def -

QAM - Most cable companies do NOT broadcast the premium channels in unencrypted QAM (at least not on purpose for extended periods of time).  This makes the HD tuners like HDHomerun and PCI cards not good for premium channels.  

Firewire 1394 STB - Cable companies will allow premium channels to be broadcast over Firewire 1394, **BUT** they typically turn 5c encryption  on, which cannot be decrypted and is DMCA violation to attempt to decrypt in US. 

CableCard - Not an option in Linux and hear it is a poor option in Vista as well.

What I did is canceled all my  premium content and saved a few $$.  It was useless to me only being able to capture SD content.  Il just rent/buy/borrow DVDs now of the series and movies.

---

### Post by tj71587 on 2007-12-26
I have a box from Comcast, where I get the premium channels.  Would it be possible to take that DVR box and link it to several PVR 150s and use that as a backend.  Then split those to other myth boxes in the house and get premium channels everywhere.  Also would that have to be wired to pass those images or would wireless suffice.  Could you go into more detail on what the IRblaster if and maybe point to a good howto.  Sorry to ask for all this, but thanks.

---

### Post by theacoustician on 2007-12-27
> **tj71587 said:**
> I have a box from Comcast, where I get the premium channels.  Would it be possible to take that DVR box and link it to several PVR 150s and use that as a backend.  Then split those to other myth boxes in the house and get premium channels everywhere.  Also would that have to be wired to pass those images or would wireless suffice.  Could you go into more detail on what the IRblaster if and maybe point to a good howto.  Sorry to ask for all this, but thanks.

Its possible, but only if you just want to capture the station in standard definition.  Also, you mention splitting it to several Myth boxes around the house.  If you're planning on having several Myth frontends running at once, you'll either need multiple set top boxes so everyone can watch what they want or be satisfied with everyone watching the same program.  Best place to start for IR control information that I've found is [http://lirc.org/](http://lirc.org/)

Its cheaper and easier if you can get Comcast to give you a cable box with firewire output.  According to the FCC, they can't refuse your request, but they may make it difficult for you to acquire one.  There's also no guarentee that the premium channels won't be scrambled over firewire.  That's a complete YMMV there.  It does consolidate control and video down to 1 cable and is much more reliable than IR (if you can get it to work) because of the bi-directional communication.

---

### Post by tedder on 2007-12-27
Does anyone have a firewire box from Comcast? I'm curious about that..

---

### Post by newlinux on 2007-12-27
I have used firewire with my cable box in 2 ways. I used to capture content digitally via firewire (used to be able to get almost every channel), but over the last year they have added 5c copy protection to my premium channels, so I don't use it in this way anymore (although I can still get ESPNHD and many other channels via firewire). Now, I use a PVR-150 to capture all content via S-Video (mainly interested in premium content), but instead of using a IR blaster, I use firewire as my channel changer. I've done this on DCT-34xx and DCT-64xx models.

---

### Post by tj71587 on 2007-12-27
I do have firewire on the back of my box, however Im sure you know that the pvr 150 has no firewire input.  Does anyone have experience with getting the premium channels off a comcast box.  The box that comcast gave us has two tuners as well.  Does that mean that I will only be able to bring one tuner with the premium channels.  My big plan involves getting one tuner with the premium channels and then adding other cards with the basic channels.  I was thinking about buying a two tuner card in order to get two tuners with the premiumc channels such as the pvr 550.  So, it would be possible to do all this over a wireless network as well or would the connection need to be wired to make it work without lag time?

---

### Post by newlinux on 2007-12-27
I have a firewire input on my computer. The PVR-150 doesn't need a firewire connection. If you can capture via firewire you don't need a PVR-150 or any tuner card. Does your computer have a firewire input?

Yes I have experience as I stated earlier. what is it you want to know about getting premiums off the comcast box? Do you want to do it via the PVR-150? you need connect video and audio output from the cable box to inputs of the PVR-150, and setup a serial, firewire, or IR blaster to change the channels. Then you can setup the appropriate input on the PVR-150 in mythtv-setup. PVR-150 recordings will be SD so you can stream them over wireless G easy. 

If you want HD capture through firewire then wireless G probably won't work consistently.

What model cable box do you have? I don't think you'll be able to access both tuners at the same time. I experimented and was unable to. Only one tuner at time for me.

---

### Post by tj71587 on 2007-12-27
I have a fireware port on the computer.  The box that I have is model dct6412.  It is an hd box, but I dont have any TV's that can do hd and it still works on the standard tv we have.  Basically, the goal is to have 3 of these set up.  One backend, which will be by our box, it will consist of the signal from the box, and two other tuners without any premium channels.  I would then like to have two frontends taht can just pick up one of the three tuners.  So two tuners will just be to watch TV and one will be to watch TV with the premium channels.  Will putting the box thru mythtv, the fireware port, work the same as the pvr 150.  I dont really understand what you mean by using firewire as the channel changer.  Is there anyway to make that standard def, and still get the premium channels unencryped.  Sorry to ask all these questions, Im completely new to this and thanks for taking all the time to help.

---

### Post by newlinux on 2007-12-27
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer#head-00fdde39847188efc7929ef908394ccf1718430a](https://help.ubuntu.com/community/MythTV_External_Channel_Changer#head-00fdde39847188efc7929ef908394ccf1718430a)

for more info on using firewire as a channel changer.

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)
for more info on capturing stations via firewire.


If you want to simply capture channels with your pvr-150 and not via firewire, then everything you capture will be convereted to standard def whether the source is HD or not.

Capturing it through firewire is not the same as capture through pvr-150. Firewire is completely dependent on what stations have 5c copy protection on. You'll only be able to to tune channels that don't have it enabled. You would then capture the channel as is (if it is an HD channel it will capture HD, SD channel it will capture SD). If all you want is standard def, go with capture via PVR-150.

---

### Post by tj71587 on 2007-12-27
Thanks for the explanation.  Just to verify, on that tutorial i would change it to a 6400 and also, using it as a channel changer would mean that if I were to connect the box to a TV, the channel would change to what I did on the Myth box.  Correct?  Thanks for helping with this, sorry if I sound stupid...

---

### Post by newlinux on 2007-12-28
> **tj71587 said:**
> Thanks for the explanation.  Just to verify, on that tutorial i would change it to a 6400 and also, using it as a channel changer would mean that if I were to connect the box to a TV, the channel would change to what I did on the Myth box.  Correct?  Thanks for helping with this, sorry if I sound stupid...

You don't sound stupid. This is where you are supposed to ask questions. So no worries.

If you are talking about the 6200ch script in the first tutorial, you don't need to change the name of the program unless you want to. It will work fine as the 6200. The difference between 62xx and 64xx is just that the 64xx boxes are DVRs. sorry, but I am not sure if that is the question you are asking, but hopefully that's the answer.


Yes, the channel should change to what you do on the mythbox (although there will be a slight delay, a second or so maybe depending on what method you use). But what you have to do is go into mythtv-setup, select the input on your PVR-150 that you are using to capture input from the cable box, and set the channel change command to 6200ch -n (whatever node you end up having to use). Use plugreport (info about it in the second tutorial) to figure out which node to use. 

Before setting it up in myth, test it command line as demonstrated in the tutorial. If it works there, it is just a matter of setting myth up right.

---

