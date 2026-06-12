---
title: "Conversion from analog to digital causing hassle help requested."
date: 2013-03-17
forum: Mythbuntu
---

### Post by whitecruiser on 2013-03-17
I have used an older p4 computer with a PVR-500 card for a couple of years and worked great with analog cable. 
I just moved to a new area that doesn't send out analog cable signal, only digital.  I decided to update the mythbuntu to the latest build 12.04 and reinstalled it over the previous one.  I can't even get tuners to receive a signal.  I am not sure what the problem is, I have run through the setup and double checked everything.  I have a MCEusb remote I know I will need to configure with this Motorola cable box to change channels, but that is secondary if I can't even get the cable signal to be seen in the PVR-500.  I have the cable out split to the two tuners but I can't even see one channel that is current on the STB.  Previously with analog cable this was a piece of cake.  Not sure where to go from here.  I am not sure if the problem is the channel list, because I haven't paid for the SD this year?  I had done a channel scan and it didn't find one channel.
--Help on how to get the tuners to receivers?
--How to get the MCEusb ir working?

---

### Post by klc5555 on 2013-03-17
> **whitecruiser said:**
> I have used an older p4 computer with a PVR-500 card for a couple of years and worked great with analog cable. 
I just moved to a new area that doesn't send out analog cable signal, only digital.  I decided to update the mythbuntu to the latest build 12.04 and reinstalled it over the previous one.  I can't even get tuners to receive a signal.  I am not sure what the problem is, I have run through the setup and double checked everything.  I have a MCEusb remote I know I will need to configure with this Motorola cable box to change channels, but that is secondary if I can't even get the cable signal to be seen in the PVR-500.  I have the cable out split to the two tuners but I can't even see one channel that is current on the STB.  Previously with analog cable this was a piece of cake.  Not sure where to go from here.  I am not sure if the problem is the channel list, because I haven't paid for the SD this year?  I had done a channel scan and it didn't find one channel.
--Help on how to get the tuners to receivers?
--How to get the MCEusb ir working?

Well, first things first. Your cable box is getting signals? You've connected a regular TV directly to the box to confirm this? The cable box is outputting analog (rather than, say, Standard Digital)  via coax, (rather than composite, or S-Video) that you're trying to connect to your Hauppauge analog tuners? 

Your first major problem is the cable box (or digital adapter) will tune to, and output one signal to one tuner. Two tuners require two cable boxes (or digital adapters). Splitting after the cable box gives you nothing, except 2 tuners receiving the same channel.

If the cable box or adapter is outputting analog via coax (rather than composite or S-video) to one of your Hauppauge tuners, the Hauppauge tuner will always remain tuned to one and only one channel: 3 or 4 depending on which channel the cable box is outputting to. I have approximately 100 digital cable stations going through three digital adapters to three analog tuners --mythtv changes channels on the digital adapters using IR blasters, but the three analog tuners themselves always stay tuned to channel 3. Since the tuning on the analog tuner never changes, there's nothing to scan. Each of the listings pages in Channel Editor for my approximately 100 digital adapter channels was added manually with "add channel" to the Video Source, and (other than the usual xmltvid and such) only tells mythtv what channel to have LIRC tune the cable box to.

So your first step, as a test, until you get LIRC working with an IR-blaster so that mythtv can change channels on the cable box on its own, is to use "add channel" in the Channel Editor to add channel 3 or 4 to a Video Source that you have set up just for this cable box. Hauppauge tuners automatically know where to tune for channels 2-99, so where the "add channel" form calls for "frequency or channel number" you supply the channel number. Using this new channel in myth with LiveTV, the tuner should see and record whatever's coming through the cable box,  much like an old-fashioned VCR.

If you can get to this stage, you'll then be ready to configure LIRC with whatever IR blaster you intend to use to talk to your cable box, so that mythtv can change channels on that box. When you get that working, you'll configure one of mythtv's included channel-change scripts for the analog tuner in Input Connections, and begin to add channels in Channel Editor, where the "frequency or channel number" item in the form will be used by mythtv to tell the channel-change script what number to pass to LIRC to,  in turn, IR blast to the cable box.

---

### Post by whitecruiser on 2013-03-17
klc5555, Thanks for the reply and the suggestions.
--Yes the coax from the cable box is getting an analog signal. I tested it on an old tv. 
--I  started with one coax connection to one of the coax connection on the  dual pvr card, but I wasn't getting anything and from the outside I  can't tell which one is which.  I decided to try to get anything to work  I would split the coax and fed the same signal to both connections just  to figure it out.  I only have one STB so I know that I will only be  able to record one at a time with this setup.
--SOME SUCCESS> my  STB uses channel 4 so I added 4 to the channel edit menu.  I am able to  see that the pvr card is now getting the signal.  I am going to work on  the IR-blaster now, but if you don't add the channels to the channel  edit menu how do you schedule shows?



Ok I have tried a few things and decided to update the post.  I guess the last thing is getting the IR remote to change the channels on the STB.  The remote I have is a MCE remote the label says RC-6, I read this was made by philips--[http://pjsbb.com/DCIM/remote.jpg](http://pjsbb.com/DCIM/remote.jpg) this is an image of it.  
It has a usb receiver and long IR unit with 3.5mm end.  image [https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcR4OxTpgPmu6OQln-WYbye_CbLrx-r2ZYwtfZvGFap2RMcDYLxCrQ](https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcR4OxTpgPmu6OQln-WYbye_CbLrx-r2ZYwtfZvGFap2RMcDYLxCrQ)   The back has two ir inputs. 

I know that the receiver is working because the remote is able to change the MYTHTV channel but is doesn't effect the STB.  I tried the digital camera trick with the ir unit to see if a signal is being sent and I don't see anything. On the remote itself I can see a flash in the digital camera so I know it is sending a signal to the receiver but it is not sending it to the ir unit.  

When I look at the setting for IR in the mythbuntu control center it looks like all the options I need should be able there.  I have tried several different configuration.  I have a simple motorola DCT-2244 box, so I tried every Motorola setting there was in the menu.  It looks like there is only one MCE setting. 

Not sure what is next.  I know that some people have written files for the commands.  I am not even sure where to start with that process.  
I am not sure how to send a command line command to see if it is working that way.

---

### Post by klc5555 on 2013-03-18
You have two IR components to worry about. The first is having the remote control talk to an IR receiver and tell Mythtv to do various things, including having LIRC change channels. You seem to have this taken care of.

The second IR task is to have LIRC transmit to an IR blaster (an IR transmitter) to transmit channel-change data to the IR port on the set-top box. You don't mention having an IR blaster installed on your machine.

Blasters come in serial port and usb flavors. As I mentioned in a post on another thread, I personally have come to rely on the usb blasters from Iguanaworks, but everyone has his own preference.


Once you have a blaster installed and configured so that you can change channels on the STB from a terminal using the LIRC-included program irsend, you set up mythtv by 1) choosing which channel-change script you wish Mythtv to use when telling LIRC to change channels. Mythtv supplies two: a perl script and a simple bash script. Pick one, and in Input Connections for your tuner(s) provide the path to your choice of "external channel changing script". 2) Also in Input Connections, set the tuner to automatically start up on the STB's signal --in your case evidently channel 4. 3) Most channel-scanning in Mythtv 0.25+ is in various stages of broken (of course), so begin adding channels in channel editor for the Video Source your pvr500 is hooked to. Since you have specified an external channel-change script, the channel number that you provide on the last page of the Add Channel form for "frequency or channel number" now merely tells Mythtv what numbers to feed to the external channel-change script to have LIRC, in turn, IR-blast them to the Set Top Box to have the STB change its channel. The PVR-500 itself will never retune.

And that's basically a sketch of the mechanical steps of the process.

---

