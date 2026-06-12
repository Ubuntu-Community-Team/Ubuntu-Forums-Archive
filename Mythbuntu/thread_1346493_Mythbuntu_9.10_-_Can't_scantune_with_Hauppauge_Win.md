---
title: "Mythbuntu 9.10 - Can't scan/tune with Hauppauge WinTV-PVR-500"
date: 2009-12-05
forum: Mythbuntu
---

### Post by lafaki on 2009-12-05
Hi,

I just installed Mythbuntu 9.10 (both backend and frontend on the same machine).

I have followed all instructions for setting up the MythTV Backend i.e. managed to find the two analogue TV tuners of my Hauppauge WinTV-PVR-500, created a video source and defined the input Connections. At that stage I am not able to scan channels (button is grayed out).

Then I followed another path. I setup Wine and TVxb and imported the xmltv.xml to the MythTV database by running the following command

[FONT="Courier New"]mythfilldatabase --file 1 /usr/local/share/TVxb/xml/xmltv.xml[/FONT]

(note that the command 
[FONT="Courier New"]mythfilldatabase --file 1 -1 /usr/local/share/TVxb/xml/xmltv.xml[/FONT]
was resulting to illegal option)

I then defined manually the channel frequencies and also setup the starting channel for both TV Tuners. 
When I select "Watch TV" in the MythTV Frontend I get a message "Please Wait" and then I am thrown back to the main menu.

Can anyone help me with this problem?  

Many Thanks!
Akis

---

### Post by pombe on 2009-12-05
I have the same card and it works fine for me.  What type of card did you specify in mythtv-setup?  Mpeg-2?

---

### Post by lafaki on 2009-12-07
Hi,

this is good news!
I will check how the card is configured and let you know.

From what I recall, I could only find in the MythTv setup the Hauppauge card as Analogue and that is what I used.
I can't remember any settings about MPEG2.

Are there any specific instructions that I need to follow?

Regards,
Akis

---

### Post by pombe on 2009-12-07
> **lafaki said:**
> Hi,

this is good news!
I will check how the card is configured and let you know.

From what I recall, I could only find in the MythTv setup the Hauppauge card as Analogue and that is what I used.
I can't remember any settings about MPEG2.

Are there any specific instructions that I need to follow?

Regards,
Akis

I dont think so.  The only ambiguous bit was the choice of MPEG-2 for the card type.  There are a couple of different settings where it looks like the card is recognized, but mpeg-2 has always been the one that worked.  

If this fails, answer back and I'll check my settings.  (this is assuming I can resolve my current issues on my mythbox...)

---

### Post by lafaki on 2009-12-08
Hi,

configuring the Hauppauge cards as MPEG2 finally worked :)
Thanks for your help!

The only problem now is that when I try to tune to some channels, the MythTV Frontend doesn't display them and throws me back to the menu. 

/Akis

---

### Post by pombe on 2009-12-08
> **lafaki said:**
> Hi,

configuring the Hauppauge cards as MPEG2 finally worked :)
Thanks for your help!

The only problem now is that when I try to tune to some channels, the MythTV Frontend doesn't display them and throws me back to the menu. 

/Akis

Glad you have a partial solution then...  Not sure what to do about the channel issue.

---

