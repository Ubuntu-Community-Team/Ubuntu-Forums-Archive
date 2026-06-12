---
title: "Using CW3000 for Mythbuntu"
date: 2008-05-26
forum: Mythbuntu
---

### Post by ZippyP on 2008-05-26
Old title:  Using CW3000 for Mythbuntu

Hello, 
Break out the popcorn for this one...:popcorn:

**I know this is long winded, I found that asking a short question always ends up with what are you running, how did you get to where you are now and how do you have it hooked up.  I figured I would answer all that first then ask the question later.  So here it goes... **

I am running a slightly modified CaptiveWorks CW3000.
I added 200GB SATA drive.  The receiver came with two [color=red]GeniaTech DVB-S PCI[/color] cards already installed.
I installed MythTV version 0.21. OK, here is where I get lost and the fun begins. No, I don't have fun getting lost. I do ask for directions. Next was the usual MythTV setup. This went pretty smooth until setting up the cards.
My next big mistake was purchasing a DVB-S /S-2 card that no one seems to support except the drivers for XP. This card is a TechnoTrend TT-Budget S2-3200. I figured when I bought this card I was going to plug it in place of one of the GeniaTech DVB-S PCI cards that were already installed in the receiver. I figured magically the card would work. Does anyone know the magic word? I have seen posts all over for this[color=red] STB0899-C5[/color] chipset card, but you would have to be a Linux/MythTV pro to figure a way to get the patches and drivers in. It looks to me that there is no step by step or easy install via Ubuntu. See below for links on this card. I usually don't give up this easily , but I gave up on this card for now. My next adventure was placing my old ATI HDTV Wonder ATSC/QAM card in the receiver replacing the S2-3200 card. I probably will end up wearing out the PCI slot soon. That was not too bad since MythTV recognizes the card. I went through the usual paces and scanned only up to 120 channels of my cable system. This is where I get lost with the ATSC card. My cable system here has more than the old expanded 120 channel system. The QAM (HDTV) channels start at 600 and go up to 700. The system uses a Scientific Atlanta Explorer 8300HD PVR box. I want to get rid of my $118 a month cable bill and use this new receiver as a replacement. Is it the card or is it the software that only allows this low channel count? After scanning the analog cable channels I went to View TV, and it went to black for a second or two then back to the menu. I only set up one card so the video source should have matched the card for watching the video. There was something definitely wrong with this picture. I posted this situation on the forum and did not get what was meant by what my setup was, hardware, software is there a way to show the setup as a text file for posting? I am not sure; I'm new to this stuff. So, here I am. The next thing was pulling out the ATSC board and placing back the DVB-s board back in, so this leaves me with the original video hardware setup.
Now to my external hardware. I have a 90cm (3ft) dish with an Invacom QPH-031 Quad LNB (two circular two Linear) and a DiSEqc four port switch, one circular port to sw1 and one linear port to sw2. One RG-6 Quad shield cable run to the top connector and the bottom loop out connector to a spectrum analyzer. Yep I own one of these. Makes the dish pointing pretty easy.

Here are the steps I took to add card 0. I hope I did this right.

[color=blue]**1.**[/color] In the Ubuntu screen, go to the System, select Administration and select MythTV backend Setup.

[color=blue]**2.**[/color] Now that I made it to the MythTV backend, I selected **Capture Cards**.
I selected **New Capture Card**, selected **Card Type :**DVB DTV capture card (v3. x) **DVB device :**0 The card information was listed as Frontend Conexant cx24123/24109 etc. etc.
**Signal Timeout** was set at 60000, ** Tunning Timout** was set at 62500.
I selected DiSEqc which shows (unconnected) I pressed enter and selected Switch from the pop-up box **Select Type of Device** selected finish.

In the **Switch Configuration** Repeat count 1, Switch type DiSEqc, Number of ports(in my case 4) selected finish. Now in the **Switch** screen I had the** (Unconnected)** line four times. I selected the first (unconnected) line pressed enter. The pop-up box again with the selection Switch, Rotor and LNB. I selected **Rotor **. **Rotor Configuration** Repeat Count 1 **Rotor Type** DiSEqc 1.3 ( Goto/USALS) **Rotor Low Speed** 1.9 **Rotor High Speed** 2.5 I placed my Lat in Lon in the lines provided then selected finish.
Now back in the **Switch** screen there was **Rotor** (unconnected). Selected (unconnected) and the pop-up **Select Type of Device** I then selected LNB. In the LNB menu I selected Linear (N. America) **LNB Voltage** already selected at Standard (voltage). **LNB LOF switch (MHz)** 0, **LNB LOF switch Low (MHz)** 10750, **LNB LOF High (MHz)** 0. Selected finish and escaped out to **Video Sources**

[color=blue]**3.**[/color] I selected **New Video Source** I gave it the name of Sat 1.
Under **Listing Grabber** is the user and password that you have selected after you sign up for Schedules Direct. 
Since I am using this for Free to Air Satellite in this setup I do not need my information typed in. I then checked **Perform EIT** **Channel Frequency Table **is at default. Selected finished and escaped out to** Select Input Connections**

[color=blue]**4.**[/color] I then selected [DVB:0](DVBInput)->Sat 1 then selected next **Connect Source to Input** **Optional Name** I put in the name Sat 1 again. **Video Source** Sat 1. Now here is where I have problems. In this case do you use under ** Use Quick Tuning**, Live TV Only, Always, or Never? I checked ** Unencrypted Channel**, checked **Allow audio only channels** and unchecked **Use DishNet Longterm EIT Data**.

Now for more questions after all this setup. Is there any popcorn left?

[color=blue]**a.**[/color] How do I move the dish to the satellite that I want after setting this up for USALS? 
[color=blue]**b.**[/color] How do I scan the transponders? Please don't tell me I have to do these one at a time.
[color=blue]**c.**[/color] Is there a satellite listing/database that can be loaded into MythTV?
[color=blue]**d.**[/color] If so, where can I find it and how does it get installed?
[color=blue]**e.**[/color] If not, is there someone working on this? I heard that [color=red]Lyngsat[/color] is setting up an accessible database like [color=red]SatcoDX[/color].
[color=blue]**f.**[/color] In reference to the ATSC card, why did it go to black after selecting View TV? 
[color=blue]**g.**[/color]Was it due to a disconnect between the sources?

I had this box for almost a month now and have not seen one HD channel on it whether it be Terrestrial or Satellite. This was a pretty expensive investment for another computer that was not needed except if it would just plug and play with my 7.1 surround system and 42 inch TV. As for the original CW3000, the software has quite a few bugs in it and was written mainly for a fixed dish package, which I have a bit more than that set up here. Quite a bit of thought was put into MythTV. MythTV has an easy to follow menu systems and a nice GUI that can be changed to your choice of themes. So, where does someone go to that has no Linux of MythTV background with all this hardware? Some posts were very useful and some were over my head. I have twenty years experience with commercial satellite systems, but this is the first time I have played around with this type of system. So, I am at an impasse now, what to do with this box.

[color=red] ** CaptiveWorks CW3000 ** [/color]
[color=green] [http://captiveworks.org/cw3000hd.php](http://captiveworks.org/cw3000hd.php) [/color]


[color=red] ** GeniaTech DVB-S PCI Card ** [/color]
[color=green] [http://hdtvonpc.com/gt_digistar.html](http://hdtvonpc.com/gt_digistar.html) [/color]


The TT-3200 card has a few links for it but as I look at it I would have to be well versed in Linux to get this to work.

[color=red] ** TechnoTrend TT-budget S2-3200 ** [/color]
[color=green] [http://www.technotrend.com/2764/TT-budget__S2-3200.html](http://www.technotrend.com/2764/TT-budget__S2-3200.html) [/color]

[color=red] ** [linux-dvb] DVB-S- and DVB-S2-streams with TT3200 ** [/color]
[color=green] [http://www.mythtvtalk.com/forum/viewtopic.php?t=4840&postdays=0&postorder=asc&start=0&sid=2b35175883e5fef420dfe952ce0a0fbb](http://www.mythtvtalk.com/forum/viewtopic.php?t=4840&postdays=0&postorder=asc&start=0&sid=2b35175883e5fef420dfe952ce0a0fbb) [/color]
[color=green] [http://linuxtv.org/pipermail/linux-dvb/2007-May/018188.html](http://linuxtv.org/pipermail/linux-dvb/2007-May/018188.html) [/color]
[color=green] [http://linuxtv.org/hg/~manu/stb0899/](http://linuxtv.org/hg/~manu/stb0899/) [/color] [color=green]check under manifest[/color] 
[color=green]  [http://linuxtv.org/hg/~manu/stb0899-c5/](http://linuxtv.org/hg/~manu/stb0899-c5/)  [/color] [color=green]check under manifest[/color]

It looks to me that they were onto something and then I guess they dropped the project, or am I wrong and this is done and working with MythTV?

[color=red] ** Lyngsat ** [/color]
[color=green] [http://www.lyngsat.com](http://www.lyngsat.com) [/color]
[color=red] ** SatcoDX ** [/color]
[color=green] [http://www.satcodx.com](http://www.satcodx.com) [/color]

Fini  ):P


Now imagine the old Star Wars credits rolling up into space.  =D>

---

### Post by ZippyP on 2010-02-05
Geeze... Almost two years later and nothing...:p

---

