---
title: "What does this mean in the mythtv wiki?"
date: 2009-10-02
forum: Mythbuntu
---

### Post by cat2005 on 2009-10-02
What does this mean in the mythtv wiki? 

[http://www.mythtv.org/wiki/Frequently_Asked_Questions#Can_I_use_MythTV_without_using_my_cable_.2F_satellite_company.27s_provided_cable_box.3F](http://www.mythtv.org/wiki/Frequently_Asked_Questions#Can_I_use_MythTV_without_using_my_cable_.2F_satellite_company.27s_provided_cable_box.3F)

**  Can I use MythTV without using my cable / satellite company's provided cable box? **

 ** United States**

 
[LIST]
[*] Normal Analog Cable: Yes, you can usually use MythTV without their provided cable box.
[*] Digital Cable, analog channels: In many cases you can tune the analog cable channels off the same line, but sometimes you will need to use the cable box.
[*] Digital Cable, digital channels: Certain cards, such as the pcHDTV 3000, can receive non-scrambled QAM-256 channels. These will generally only be your local HDTV channels. For all other channels you will need the cable box and an analog capture card.
[/LIST]

Did you read that?  It states "Digital Cable, Analog Channels".  How can one have analog channels if one has digital cable?  Am I missing something or is this an error?

I would appreciate your thoughts!

---

### Post by azmyth on 2009-10-02
I can get channels 1-90 without a cable box once I want to see channels 90 and above I must use a cable box controlled by a blaster or firewire. My cable provider refers to 1-90 as analog and everything and above a digital.

---

### Post by tgm4883 on 2009-10-02
> **cat2005 said:**
> What does this mean in the mythtv wiki? 

[http://www.mythtv.org/wiki/Frequently_Asked_Questions#Can_I_use_MythTV_without_using_my_cable_.2F_satellite_company.27s_provided_cable_box.3F](http://www.mythtv.org/wiki/Frequently_Asked_Questions#Can_I_use_MythTV_without_using_my_cable_.2F_satellite_company.27s_provided_cable_box.3F)

**  Can I use MythTV without using my cable / satellite company's provided cable box? **

 ** United States**

 
[LIST]
[*] Normal Analog Cable: Yes, you can usually use MythTV without their provided cable box.
[*] Digital Cable, analog channels: In many cases you can tune the analog cable channels off the same line, but sometimes you will need to use the cable box.
[*] Digital Cable, digital channels: Certain cards, such as the pcHDTV 3000, can receive non-scrambled QAM-256 channels. These will generally only be your local HDTV channels. For all other channels you will need the cable box and an analog capture card.
[/LIST]

Did you read that?  It states "Digital Cable, Analog Channels".  How can one have analog channels if one has digital cable?  Am I missing something or is this an error?

I would appreciate your thoughts!

My guess is that is for people who subscribe to a cable companies "Digital Cable" package and find that some of their channels are analog.

---

### Post by cat2005 on 2009-10-03
> **azmyth said:**
> I can get channels 1-90 without a cable box once I want to see channels 90 and above I must use a cable box controlled by a blaster or firewire. My cable provider refers to 1-90 as analog and everything and above a digital.


That does make sense, thanks!

---

### Post by Lepy on 2009-10-04
I have the digital starter package with comcast. Using my HVR-1600, I split the wall signal. 

On the analog side, I pickup channels 2 - 70, and on the ATSC side, I pickup all of the channels I do on analog + clear QAM HD networks and a few other digital channels like CSPAN2 and 3, Univision, Style.

Now, if I could only get the ATSC signals to stop stuttering.

---

### Post by cat2005 on 2009-10-04
> **Lepy said:**
> I have the digital starter package with comcast. Using my HVR-1600, I split the wall signal. 

On the analog side, I pickup channels 2 - 70, and on the ATSC side, I pickup all of the channels I do on analog + clear QAM HD networks and a few other digital channels like CSPAN2 and 3, Univision, Style.

Now, if I could only get the ATSC signals to stop stuttering.


How well do you like your 1600?  That is one of several models I am contemplating.

---

### Post by cat2005 on 2009-10-05
Bump:  I just noticed the following -

"_Digital Cable, digital channels_: Certain cards, such as the pcHDTV 3000, can receive non-scrambled QAM-256 channels. These will generally only be your local HDTV channels. For all other channels you will need the cable box and an _analog capture card_."

I underlined the parts that caught my attention.  If I am receiving "digital cable, digital channels" then why would I need an "analog capture card"?  Wouldn't I need a "digital capture card"?

Doesn't the cable box "unscramble" the "scrambled" digital signal, therefore making it possible to view and record via a digital capture card?

---

### Post by tgm4883 on 2009-10-05
> **cat2005 said:**
> Bump:  I just noticed the following -

"_Digital Cable, digital channels_: Certain cards, such as the pcHDTV 3000, can receive non-scrambled QAM-256 channels. These will generally only be your local HDTV channels. For all other channels you will need the cable box and an _analog capture card_."

I underlined the parts that caught my attention.  If I am receiving "digital cable, digital channels" then why would I need an "analog capture card"?  Wouldn't I need a "digital capture card"?

Doesn't the cable box "unscramble" the "scrambled" digital signal, therefore making it possible to view and record via a digital capture card?

No, a cable box unscrables the signal, but outputs an analog signal, not a digital signal.

---

### Post by Lepy on 2009-10-05
> **cat2005 said:**
> How well do you like your 1600?  That is one of several models I am contemplating.

I like it. It has one analog and one digital tuner, and the the MCE version I got came with a nice usb ir receiver and remote that work out of the both in mythtv. Also, the set-up was really easy following the wiki.

My only complaint is that I'm getting some jittery, prebuffering pause related playback and recording on the digital side. However, I'm fairly certain it is not a fault of the card, rather misconfiguration or other hardware on my side.

---

### Post by Jeconti on 2009-10-06
> **Lepy said:**
> 
My only complaint is that I'm getting some jittery, prebuffering pause related playback and recording on the digital side. However, I'm fairly certain it is not a fault of the card, rather misconfiguration or other hardware on my side.

I'm having some of the same issues using my Dish Network STB inputing to the S-Video connection. You think a RAM upgrade up from 1 gig will help?

---

### Post by chipppy on 2009-10-06
Good Evening

in answer to the original question about getting analog channel froma digital cable.

there are two very different method of transmitting a signal.  Analog and digital every knows about the different types.  If you want specfics then do a web search.

what most people dont understand is that usually the analog is transmitter within a lower frequency range and the digital is transmitted within a higher frequency rage.

The cable can handle both frequency ranges so therefore both signal types.

It does get a lot lot more complex then that but that is the basic answer to how this is possible.

Cheers
chipppy

---

### Post by Lepy on 2009-10-06
> **Jeconti said:**
> I'm having some of the same issues using my Dish Network STB inputing to the S-Video connection. You think a RAM upgrade up from 1 gig will help?

I don't know. What are the specs of your machine? Is the jittery playback happening with both the analog (s-video input) and digital sides of the card? Does it appear when viewing the STB directly or only when recording/watching using mythtv

In my machine, using 1 gig and 1.5 gigs of ram still results in jitters. However, my problem is using the ATSC tuner (watching both SD and HD). 

My HVR-1600 records and watches analog fine (with some signal noise) through the tuner, but I imagine that the s-video input would be fine too.

Check [my thread](http://ubuntuforums.org/showthread.php?p=8032845#post8032845) and see if you are having similar problems.

---

### Post by cat2005 on 2009-10-06
> **tgm4883 said:**
> No, a cable box unscrables the signal, but outputs an analog signal, not a digital signal.
 
tgm4883,
 
So, if I understand correctly, the cable box receives digital but outputs analog? 
 
Is that because I am trying to get the output into mythtv (mythbuntu), or would this be the case even if I used a regular TV / cable box setup?
 
Sorry, now I am extra confused. Are you stating I would be paying for digital but would be viewing analog?

---

### Post by tgm4883 on 2009-10-06
> **cat2005 said:**
> tgm4883,
 
So, if I understand correctly, the cable box receives digital but outputs analog? 
 
Is that because I am trying to get the output into mythtv (mythbuntu), or would this be the case even if I used a regular TV / cable box setup?
 
Sorry, now I am extra confused. Are you stating I would be paying for digital but would be viewing analog?

If you hook up the cable directly to a digital tuner (in a TV, computer, whatever) you will most likely only get the local channels.

If you hook up your TV or computer to your cable box via coax, svideo, composite or component, that is all analog.

If you hook up your TV or computer to your cable box via DVI or HDMI, then you will be outputting a digital signal from your box. There is no HDMI or DVI tuners I know of though.

Keep in mind that the picture will look better coming from your box, because the signal is digital except for the last 3 feet.

---

### Post by cat2005 on 2009-10-06
> **tgm4883 said:**
> If you hook up the cable directly to a digital tuner (in a TV, computer, whatever) you will most likely only get the local channels.
 
If you hook up your TV or computer to your cable box via coax, svideo, composite or component, that is all analog.
 
If you hook up your TV or computer to your cable box via DVI or HDMI, then you will be outputting a digital signal from your box. There is no HDMI or DVI tuners I know of though.
 
Keep in mind that the picture will look better coming from your box, because the signal is digital except for the last 3 feet.
 
 
tgm4883,
 
I think I understand.  Is this summary correct:
 
If I use a TV tuner on my computer, then I will ultimately _watch_ analog. I could _receive_ digital but I will ultimately _watch_ analog because the last 3 feet "downgrades" to analog.
 
Is that correct?
 
As a logical follow-up, then which of the following would give me the best analog video and audio stream:  coax, svideo, composite or component?
 
Thank you again for your explanations!

---

### Post by tgm4883 on 2009-10-06
> **cat2005 said:**
> tgm4883,
 
I think I understand.  Is this summary correct:
 
If I use a TV tuner on my computer, then I will ultimately _watch_ analog. I could _receive_ digital but I will ultimately _watch_ analog because the last 3 feet "downgrades" to analog.
 
Is that correct?
 
As a logical follow-up, then which of the following would give me the best analog video and audio stream:  coax, svideo, composite or component?
 
Thank you again for your explanations!

Yes that is correct.

From best to worst. 

Component > svideo > composite > coax (I think coax is last anyway)

Note: Component is the only one that can do HD. Also, the only component tuner is the Hauppauge HD-PVR

---

### Post by cat2005 on 2009-10-06
> **tgm4883 said:**
> Yes that is correct.

From best to worst. 

Component > svideo > composite > coax (I think coax is last anyway)

Note: Component is the only one that can do HD. Also, the only component tuner is the Hauppauge HD-PVR


tgm4883,

Of those "best to worst" cables you mentioned:  Do they handle both video and audio, or must I obtain a separate audio cable?

Thank you again!

---

### Post by tgm4883 on 2009-10-06
> **cat2005 said:**
> tgm4883,

Of those "best to worst" cables you mentioned:  Do they handle both video and audio, or must I obtain a separate audio cable?

Thank you again!

The only one that has audio is coax

---

