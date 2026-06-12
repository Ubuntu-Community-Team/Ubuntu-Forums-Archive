---
title: "Bluetooth tethering with Droid X fails after initial success"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by Briareus on 2011-05-14
Hey, everyone.  First-time poster turning to your collective wisdom in hopes of a solution. =)

I have a Droid X. I have a slightly Frankensteined laptop where the wireless module is not working but the Bluetooth module is, a minty-fresh 11.04 installation, and I've heard that Bluetooth tethering works far better in Ubuntu than it does in Windows (where it worked for me not at all - I was only able to connect to the phone over a USB tether with PDANet).

So I go into the default Bluetooth applet in Ubuntu, choose "Set up new device...", do the PIN setup - as soon as I enter the PIN on the phone, the computer recognizes this and moves on with the setup. I select both the Network Access Point and the DUN boxes, it asks me a couple questions about my carrier, and we're done. I see two new choices in the Network Manager, I click on the one for my phone's data connection (can't remember the name now), and it connects - I visit a few webpages to verify that it worked. The connection is abysmally slow, but it's still a success in my book.  So far, so good; I put the laptop to sleep and go do something else.

This morning, the connection is not working when I wake it up - I figured it would re-connect, but it's not as though one click in the Network Manager applet is a major chore.

I open up the Network Manager. The connections from yesterday are no longer there. I check the phone. Bluetooth is still enabled. On the laptop, in the applet's "Preferences" window, the phone is listed both the plug icon and the Bluetooth symbol + lock icon:

[IMG]http://img163.imageshack.us/img163/1287/78076323.png[/IMG]

(I tried finding out what specifically these are supposed to represent, without much luck - I'm assuming an active connection and a pairing, respectively. I *think* the Bluetooth icon was not greyed out then, but not 100% sure.)

I try removing removing the phone from my list of devices and pairing with it again. This time, when the PIN window comes up and I enter the PIN on my phone, the laptop immediately shows up on the phone in the device list as "Paired but not connected", but the prompt on the laptop *does not* go away and move on to the next step - it just stays there for approximately a minute, and then changes to a window saying "Device Setup Failed". After leaving that window, the phone shows up in the device list on the laptop with a greyed-out Bluetooth icon.

That's about all I can get out of the default applet. When I try to initiate a pairing from the phone, a prompt comes up asking me to specify a PIN and, if I do nothing, it goes away after ~7 seconds with a message saying "There was a problem pairing with bluetooth device."  If I enter a PIN before it goes, it proceeds with the request, I get a prompt on my laptop, enter the PIN there - and end up with exactly the same result: phone listing + grey Bluetooth icon on my laptop, laptop "paired but not connected" on my phone.

After some more experimentation yielded nothing new, I decide to try something else and install the Blueman Bluetooth Manager from the Software Center.

Condensing for readability:

**Pairing from phone**: "Paired but not connected" on the phone, phone shows up in both the Gnome applet and Blueman.

**Pairing from Blueman**: "Paired but not connected on the phone", Blueman shows "Pairing" for a couple of minutes after I enter the PIN on the phone, then reports "Did not receive a reply. Possible causes include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken." Phone also shows up in the applet list.

**Running discovery from Blueman and, *without pairing*, right-clicking the phone and selecting "Add Device":** Phone added to both Blueman and the applet's context menu, but *not* to the list in the applet's "Preferences" window. The laptop entry (unsurprisingly) does not show up on the phone. The context menu for the phone in Blueman looks like this at this point:

[IMG]http://img23.imageshack.us/img23/7588/46884161.png[/IMG]

Choosing either "Dialup Networking" or "Network Access Point" brings up a prompt that says

> **Device '*phone name*' wants to pair with this computer**
Please enter the PIN mentioned on device '*phone name*' (*phone MAC* address)

Entering anything at all, including the PIN used in the last pairing attempt, immediately gives this message:

> Connection Failed: Network Manager Failed to activate the connection.

Nothing whatsoever comes up on the phone during all this. (Note: this is inconsistent. After turning on discovery on the phone and choosing "Dialup Networking" or "Network Access Point" during the discovery window *as well as some time after the discovery window ends*, the PIN prompt comes up on both the phone and the laptop.)


...this is starting to feel like a flowchart from hell and there's still a number of special cases I've seen and haven't covered, so I'll briefly summarize and let you ask for more detail where you feel it's needed.

TL;DR: After the single initial successful pairing, the Gnome Bluetooth applet cannot establish a pairing with my Droid X; the Blueman Bluetooth Manager sometimes pairs successfully and reports successful DUN (showing on the phone as "Connected to phone modem") and NAP (ditto as "Connected to panu") connections (which *sometimes* get immediately disconnected and *sometimes* show up in **iwconfig**, still unable to reliably reproduce the latter), but the connection supposedly established thereby does not appear to do anything. Please advise.

---

### Post by Briareus on 2011-05-14
Also, let me know if this is not the right forum for this question. >_>  This seemed like the best fit our of several possibilities, but I'm still learning my way around here.

---

### Post by ChrisNZ on 2011-05-20
Hi, I hear your frustration!

I have a android phone as well. I get a similar issue using Ubuntu 11.04 Natty, with Blue Proximity. I get "paired but not connected and not trusted" on my phone!
Hope you find some answers on this one.

---

### Post by khurtsiya on 2012-03-18
I paired HTC Sensation to my Ubuntu 11.10 and first time sent 9 of 10 images to laptop. Since that I am not able to send anything - sending fails.

First time there was prompt (receive or cancel) and now the dialog box does not appear. Can anyone help with this?

---

