---
title: "Home DVD player"
date: 2010-01-26
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-26
I have a home DVD player with a remote that was intended to hook up to a TV via either S-video or RCA cables.  Can this be played through my mythbuntu pc...maybe wire it in with a RCA-usb cable?

---

### Post by LowSky on 2010-01-26
one of these type of devices might work or a TV tuner card
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380047+1685342852&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=47&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380047+1685342852&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=47&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by klc5555 on 2010-01-26
> **linuxhippy said:**
> I have a home DVD player with a remote that was intended to hook up to a TV via either S-video or RCA cables.  Can this be played through my mythbuntu pc...maybe wire it in with a RCA-usb cable?

I used to use mine connected to my PVR-150 tuner. Worked fine, of course, save that myth buffers the input from the DVD player across the recording drives the same as it does any other tv signal. So that there would be a 5-20+ second delay before seeing the effects of a remote-control button press for the DVD player. For this reason I tend to prefer to have the thing connected directly to the tv.

---

### Post by linuxhippy on 2010-01-26
> **klc5555 said:**
> I used to use mine connected to my PVR-150 tuner. Worked fine, of course, save that myth buffers the input from the DVD player across the recording drives the same as it does any other tv signal. So that there would be a 5-20+ second delay before seeing the effects of a remote-control button press for the DVD player. For this reason I tend to prefer to have the thing connected directly to the tv.

My tuner card has an s-video input and my DVD player has an s-video output...how can I configure mythbuntu to read the video source from my s-video input on my tuner card?

---

### Post by klc5555 on 2010-01-27
> **linuxhippy said:**
> My tuner card has an s-video input and my DVD player has an s-video output...how can I configure mythbuntu to read the video source from my s-video input on my tuner card?

Basically, in the back end, set up a new Video Source that uses no schedules grabber. Call it "DVD player" or whatever. In Input Connections, all inputs on your card should be visible, including the S-video input. Connect the Video Source "DVD player" to this S-Video Input Connection. Put the card's S-video input and the card's other active input into the same recording group, so that myth doesn't try to have the card record and dvd-watch at the same time. You can switch from tv to DVD player and back from "switch sources" or "switch input" in the usual on-screen menu "m"

---

### Post by linuxhippy on 2010-01-27
so then would "watch TV" show my DVD film?

---

### Post by tgm4883 on 2010-01-27
> **klc5555 said:**
> Basically, in the back end, set up a new Video Source that uses no schedules grabber. Call it "DVD player" or whatever. In Input Connections, all inputs on your card should be visible, including the S-video input. Connect the Video Source "DVD player" to this S-Video Input Connection. Put the card's S-video input and the card's other active input into the same recording group, so that myth doesn't try to have the card record and dvd-watch at the same time. You can switch from tv to DVD player and back from "switch sources" or "switch input" in the usual on-screen menu "m"

Actually I think you need to bind the inputs.

---

### Post by klc5555 on 2010-01-27
> **linuxhippy said:**
> so then would "watch TV" show my DVD film?

Essentially. Livetv is where you'd access the menu to switch the source. 

It's been close to a year and a half since I had my DVD player piped through my pvr-150. I didn't like the buffering delay when using the remote, and of course playing DVDs interfered with the recording schedule and used computer resources unnecessarily. And playing back through a pvr-150 limits you to the pvr-150's picture quality. So after a few months I hooked the dvd player directly to the tv, and I don't remember whether I ever bothered to define a starting channel for the input/video source or not. Doing so gets rid of the "Tuner x is set to start on Add channel, which doesn't exist" error message when exiting the backend setup.

---

### Post by linuxhippy on 2010-01-28
Is there another way to view a stand alone DVD player with a monitor than putting it through my capture card?  IF I had a cable that would get it directly into my monitor, would the monitor be able to display the DVD images without an xorg.conf?

---

