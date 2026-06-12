---
title: "Mythbuntu + pchdtv card + dvico dual express + hdhomerun = 10 inputs?"
date: 2009-02-11
forum: Mythbuntu
---

### Post by bwooster0 on 2009-02-11
I am using Mythbuntu 8.10.

At first I used a hdhomerun box with it and it showed up as input 1 & 2 when I tried to schedule recordings and chose to use a specific input it showed me that I had two choices: input 1: MPEGTS and input 2: MPEGTS

I added in a pchdtv pci tuner card and gained input "4: DVBINPUT" AND ALSO input :5: DVBINPUT"

Somehow adding in the one tv tuner card got me two additional input choices.

I recently added a pci DVICO HDTV7 Dual Express card and I now have more inputs that are listed as:

input "6: DVDBINPUT"
input "7: DVDBINPUT"
input "8: DVDBINPUT"
input "9: DVDBINPUT"
input "10: DVDBINPUT"
input "11: DVDBINPUT"

Why did adding the pchdtv card add 2 inputs?

Why did adding the Dual express card add 6 inputs?

Are all these inputs real? If I chose to use say, input 11 on the dual express card will the recording work?

Thanks for any help.

---

### Post by bwooster0 on 2009-02-22
I think I found out why Mythtv thought that I had all those inputs.

I think it was because when used the "Capture Cards" Mythtv set up screen some of the entries listed the cards as having "Max recordings" set to "2"

I redid my tuner card setups and made sure that the max recordings was set to 1

For the FusionHDTV7 when I went to the "Capture cards" part of Mythtv set up I

1) added in my card as a "DVB DTV capture card(v3.x)" with device id 1
2) I then went to the "recording options" menu and set Max recordings to 1
3) I turned off the "active EIT scan" option (I have a schedules direct account)

Then I repeated the above steps adding in the same card with device id 2

Now in Mythtv the number of tuner inputs is correct

---

### Post by blackoper on 2009-02-22
if you have hd channels sharing a frequency, multiple inputs on a dvb card is a good thing. I have two dvb cards and I have two inputs on them now (added them both with 1, then came back and set it to 2 to "stagger" their input names). This comes in handy because two sets of my hd channels share the same frequency so it can record both channels at once on one card and myth does this automatically. That's why by default dvb cards are set to 2 inputs when you go to add them. 
mythtv wiki on it is here: [http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex]("http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex")

---

