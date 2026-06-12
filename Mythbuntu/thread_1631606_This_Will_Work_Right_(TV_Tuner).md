---
title: "This Will Work Right (TV Tuner)"
date: 2010-11-26
forum: Mythbuntu
---

### Post by Lone_Joker on 2010-11-26
Okay so I was thinking about buying a [Hauppauge HVR-1850]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116015") and using it with MythTV.

As far as I know the only input that works under Linux is the digital input. I'm right, right?

My main concern is recording TV. I know that this card can not receive encrypted channels (channels are what is encrypted right?). But would I be able to record encrypted channels if I connected this to the STB given to me by Comcast? I'd also like to split the connection from my STB to my MythBox, is there a certain type of splitter that I would require?

Will MythTV find channels just fine even if it's behind an STB, or will I need to use something like scte65scan? Can I get MythTV to get the guide data from the STB or would I have to use Schedules Direct or zap2it? 

Anybody else have this card? Did you get the remote and blaster to work? Any guides on setting this card up?

---

### Post by thatguruguy on 2010-11-26
Have you considered another tuner, such as the 950Q? It supports both analog and digital.

---

### Post by Lone_Joker on 2010-11-30
I need a tuner card with hardware encoding because I plan on installing this on a machine with an atom processor (1.66GHz).

Does anybody have this card working with MythTV?

---

### Post by Senkoboy on 2010-11-30
> **Lone_Joker said:**
> I need a tuner card with hardware encoding because I plan on installing this on a machine with an atom processor 

Digital signals are already digital, no encoding required.

---

### Post by theluddite on 2010-11-30
I looked into this very same thing a while ago for my Hauppage 150.  Firstly, I found that with my cable service provider (Shaw in Canada) that their digital signal is encrypted, which forced you to either rent their STB for an extra $15 a month or go buy one for $300.  This is likely the same with ComCast.  Further, there were issues getting the unencrypted signal from the STB to the card.  You'll need to check that your STB has a digital out, most likely in the form of a firewire connection.  In my research I seem to recall that you won't have any luck getting the decrypted HD channels into your TV Tuner at all.  I dispensed with digital altogether and just use the analogue signal, which (in Canada) remains for channels 1-50 with my cable provider.  It's not digital quality, but I watch most of my TV via HD downloads anyway -- so for me it's not an issue.

As for the channels, I didn't notice anything in the MythTV configuration to use the sched from your STB.  My myth box uses Schedules Direct just fine and from my recollection it's a ridiculously low price.

---

### Post by Lone_Joker on 2010-11-30
> **Senkoboy said:**
> Digital signals are already digital, no encoding required.

Oh, I thought they were the same as analog just higher quality. I feel dumb... :oops:

> **theluddite said:**
> Further, there were issues getting the unencrypted signal from the STB to the card.  You'll need to check that your STB has a digital out, most likely in the form of a firewire connection.  In my research I seem to recall that you won't have any luck getting the decrypted HD channels into your TV Tuner at all.

What problems did you have? Do you know if it was specific to your STB?

---

### Post by Decatf on 2010-11-30
You will able to record channels by connecting an STB to the tuner card  (assuming proper Linux support) but keep in mind it will **not**  be in HD / digital. This tuner card along with most others only  do analog (SD) video input. The HD part of the tuner card refers to the tuner  itself. In other words the part that receives the raw television signal can handle HD channels the part that takes video input (via S-Video or Composite) is in SD.
   
  You can only use the tuner (when connecting the coaxial TV cable to the  tuner) to receive raw unencrypted channels as mentioned previously. Doing  this is basically using your computer in place of the STB except you  won't receive the encrypted channels.
   i.e. *An STB  (receives **encrypted** channels)-> TV/Monitor* is similar to *A Computer w/Tuner (receives **unencrypted** channels only) - > TV/Monitor*
  
Now by connecting the STB to the tuner you will still get the encrypted  channels (since the STB is handling the raw TV signal) but you will be  recording through the analog inputs of the tuner. 
   i.e. *STB   (receive encrypted channels) -> Analog video ->  Computer w/Tuner (receive analog signal) -> TV/Monitor*
In other words this option is not using the "tuner" part of the tuner card at all. It is simply using it to get analog video input (a feature a lot of video cards already have).
 
 If that setup is fine for your needs then you're good to go. I'm  pretty sure you can't get guide data of the STB but I do know that some  STBs can be controlled through firewire/USB (channel changing and stuff). Otherwise you will have to control the STB with the good ol' remote.

I hope that makes sense.


Some STBs do support recording digital video through a firewire connection but our good friend encryption comes up again. Some cable cos encrypt this too. Some providers don't encrypt at all, some only encrypt some channels, some encrypt them all. If you record via firewire you do not need a tuner at all. (Discussion getting around this type of encryption can get dicey. I don't know if it's allow on this forum)


You won't find many digital / HD video input cards around and if you do they have been quite expensive in the past. A plain old device like this would basically allow anyone to easily rip HD content of anything TV, Bluray, etc.

---

### Post by Lone_Joker on 2010-11-30
Ok so what exactly would be happening if I connect the tuner to an STB?

Wall->STB, this step will unencrypt any channels encrypted by Comcast.
STB->Tuner Card, tuner card only acts as video capture (tuning done by STB) which is why I would still need to change the channel on the STB (IR blaster) and not from the tuner card. The STB also converts digital signals to analog, right?

So what I need is a tuner card that I can use to pick up analog signals, right? Or a video card that will pick up analog signals, which I don't have.

EDIT:
If it helps, my STB is a Motorola DCT2000 (no firewire).
I was also wondering if the included IR blaster will work with Linux. I've been using Google, but I haven't found a solid answer yet.

---

### Post by Decatf on 2010-11-30
Ok the DCT2000 isn't an HD box so most of my previous post about that HD crap doesn't apply anyways :p

So connecting the STB to a tuner card with S-Video or Composite should work. From a quick google it looks like people even control the STB from the serial port.

---

### Post by Lone_Joker on 2010-11-30
Alright, that's less to worry about. But does an STB convert digital signal to analog signal?

And I was thinking about sharing the connection from the STB between the tuner and my TV. I only want to use the tuner for recording (don't care about live TV). I'm going to have to split the connection but I'm not sure what these cables are called. Splitters? Y-Adapters? Google AWAY..

Hmm... seems like the HVR 1800 doesn't work completely under Linux. Too bad the HVR 1600 isn't PCIe. I hope I can find somebody that has this card working under Myth D:

---

### Post by Senkoboy on 2010-12-01
> **Lone_Joker said:**
> Oh, I thought they were the same as analog just higher quality. I feel dumb... :oops: 

No dumb questions on here, just a lot to learn.

A Hauppage PVR-150 is a well supported analog card, you need
an open pci slot and you would have to set up a blaster to change channels on your STB. 

I have Suddenlink cable, our channels up to 73 are unencrypted QAM.  I use a ATI HDTV Wonder card to recieve them. It will recieve HD OTA or HD unencrypted QAM also.

---

### Post by Lone_Joker on 2010-12-01
My motherboard only has 1 PCIe x16 slot (mini-itx) so the pvr-150 won't work for me. At least PCIe x16 works will all PCIe types

Maybe I should look into the 950Q like the first poster said...

---

### Post by nickrout on 2010-12-03
What you really want is an hdpvr which takes a hi def analogue signal from your STB and records it to h.264. It requires only a USB connection to the computer.

---

### Post by Ubu_Fester on 2010-12-04
FWIW, I have the Hauppauge hvr 1600 working under Linux/Mythtv.

---

