---
title: "remap button on remote (not LIRC)"
date: 2010-11-29
forum: Mythbuntu
---

### Post by davidstoll on 2010-11-29
I have an MCE compatible remote control that is detected as a keyboard/mouse (not LIRC based).  I would like to remap a button on the remote to a different key.  How do I do that?

The "back" button does not act like other MCE IR remotes in MythTV.

I also want to assign the colored buttons at the bottom to shell scripts which I have already created.  I can do this with IRexec, but not with a non-LIRC remote.

Here is the remote I have.
[http://www.amazon.com/Windows-Control-Infrared-Receiver-Ultimate/dp/B00224ZDFY/ref=sr_1_1?ie=UTF8&qid=1291045314&sr=8-1](http://www.amazon.com/Windows-Control-Infrared-Receiver-Ultimate/dp/B00224ZDFY/ref=sr_1_1?ie=UTF8&qid=1291045314&sr=8-1)

Thanks

---

### Post by winewood on 2010-11-29
I have looked at your product.  A reviewer on Amazon stated that the keys could not be remapped.  Its a low end model, this is expected.

I am not sure how it broke with the standard MCE layout if it calls itself a MCE, all buttons usually follow a standard.  Perhaps another botton is mapped with "back" in an unfamiliar location?

If using 'irw' does not show any commands going into it, then I know nothing that can help.  However, when you type 'irw' on a command line and you see codes, then I do not see why you could not map those codes to any action or script you wanted.  (if they are to function key "back" or letter "m" such as a keyboard mapping)

This remote is a standard IR transmitter, the map problem and detection mapping may be due to the ir receiver and driver.  I found a SIIG usb IR receiver that ships with their remotes maps as needed and they are cheap.  Is it unreasonable to just take it back for another MCE remote?  Seems like a lot of work for a $13 part.

Edit: I found that if you look under "Vista MCE Remote" by SIIG, it will include a USB IR receiver that works well.  I suggest buying this one, and seeing if both work off the same IR receiver the way you want.  This way the wife/girlfriend has one or you have a backup.

---

### Post by davidstoll on 2010-11-29
I didn't actually buy it from Amazon, but saw that they sold it, so that's why I linked to it.

So, basically with the introduction of 10.10, the whole Lirc system is really screwed up.  Streamzap has serious issues.

What is the best MCE remote that has extra colored buttons (so I can program custom scripts)?  Streamzap is no longer a good option.

I have an MCE IR6 remote, but don't remember where I got it and can't find it anywhere (it is black and shaped like an hour glass).

Anyway, I need a good MCE remote for MythTV.

Thanks!

---

### Post by larsolav on 2010-11-29
I have both the streamzap and the remote you linked to. I'll be putting them on ebay myself as I recently hit jackpot with this guy:
[http://cgi.ebay.com/Microsoft-MCE-Media-Center-Remote-Control-Complete-Kit-/320581651052](http://cgi.ebay.com/Microsoft-MCE-Media-Center-Remote-Control-Complete-Kit-/320581651052)
or from Dell (should be the same thing, I believe):
[http://cgi.ebay.com/NEW-Dell-Microsoft-MCE-Media-Center-Remote-Control-Kit_W0QQitemZ150519100034](http://cgi.ebay.com/NEW-Dell-Microsoft-MCE-Media-Center-Remote-Control-Kit_W0QQitemZ150519100034)

or just search for "Remote Control Kit for Media Center" on Ebay.

This remote worked for me out of the box (I believe it has an RC6 MCE IR receiver) and has a decent range and even worked with my Next Generation Remote Control Extender...

---

### Post by davidstoll on 2010-11-29
> **larsolav said:**
> I have both the streamzap and the remote you linked to. I'll be putting them on ebay myself as I recently hit jackpot with this guy:
[http://cgi.ebay.com/Microsoft-MCE-Media-Center-Remote-Control-Complete-Kit-/320581651052](http://cgi.ebay.com/Microsoft-MCE-Media-Center-Remote-Control-Complete-Kit-/320581651052)
or from Dell (should be the same thing, I believe):
[http://cgi.ebay.com/NEW-Dell-Microsoft-MCE-Media-Center-Remote-Control-Kit_W0QQitemZ150519100034](http://cgi.ebay.com/NEW-Dell-Microsoft-MCE-Media-Center-Remote-Control-Kit_W0QQitemZ150519100034)

or just search for "Remote Control Kit for Media Center" on Ebay.

This remote worked for me out of the box (I believe it has an RC6 MCE IR receiver) and has a decent range and even worked with my Next Generation Remote Control Extender...


I have seen that model, but I'm looking for a remote with the 4 colored buttons (typically at the bottom) for customizing.

I have scoured ebay, but maybe I have the wrong keywords...?

---

### Post by larsolav on 2010-11-29
Ah yes, did not catch that. How about customizing the buttons between the mute button and the first row of numbers? (those are buttons not found on the streamzap)

---

### Post by davidstoll on 2010-11-29
> **larsolav said:**
> Ah yes, did not catch that. How about customizing the buttons between the mute button and the first row of numbers? (those are buttons not found on the streamzap)

I suppose that's a possibility.  What are they?  Do they have text?  The only problem there is that non-techies also use this.  It's easier to have the 4 color buttons on each remote for each frontend so they can easily remember what they do....at least that's what I've setup thus far.  To change would be very frustrating for them.  :(

What about this one?

[http://cgi.ebay.com/Dell-C2615-Remote-Control-Kit-Media-Center-NEW-/250661065330?pt=LH_DefaultDomain_0&hash=item3a5c905272#ht_3006wt_986](http://cgi.ebay.com/Dell-C2615-Remote-Control-Kit-Media-Center-NEW-/250661065330?pt=LH_DefaultDomain_0&hash=item3a5c905272#ht_3006wt_986)

---

### Post by kyphos on 2010-11-29
> **davidstoll said:**
> I have an MCE compatible remote control that is detected as a keyboard/mouse (not LIRC based).  I would like to remap a button on the remote to a different key.  How do I do that?

The "back" button does not act like other MCE IR remotes in MythTV.



@davidstoll,
I also have a remote+rcvr that looks (to Ubuntu) like a USB keyboard.  The remote is a dinky credit-card sized device with membrane buttons. The IR receiver is about 2" x 1" and plugs into a USB port.  It was bundled with an Asus tuner card.  

Like you, I found the 'back' function (a button labeled CLOSE) on the remote keypad wasn't compatible with Myth's 'back' command.  A few other keypad buttons were also screwed up. I've just finished tweaking the key mapping using myth frontend (Utilities-Setup/Edit Keys). I added additional keystrokes to the key mapping tables so the 'keystrokes' sent by the remote would also activate the desired command. For example, my CLOSE button sends a ctrl-K. Each myth command can map up to four different keystrokes (in the Edit Keys tables), so you should be able to retain the functionality of a full keyboard while adding new keystrokes needed for your remote. 

I don't actually use the Asus credit-card remote for day-to-day viewing. My preferred command/control device is an MX-500 unified remote control. It has a learning function, so I can train any button on it (using the various device remote controls)  to do whatever I want: Myth commands, Sony Bravia commands, SA cable box commands, audio receiver commands, etc.

---

### Post by davidstoll on 2010-11-30
> **kyphos said:**
> @davidstoll,
I also have a remote+rcvr that looks (to Ubuntu) like a USB keyboard.  The remote is a dinky credit-card sized device with membrane buttons. The IR receiver is about 2" x 1" and plugs into a USB port.  It was bundled with an Asus tuner card.  

Like you, I found the 'back' function (a button labeled CLOSE) on the remote keypad wasn't compatible with Myth's 'back' command.  A few other keypad buttons were also screwed up. I've just finished tweaking the key mapping using myth frontend (Utilities-Setup/Edit Keys). I added additional keystrokes to the key mapping tables so the 'keystrokes' sent by the remote would also activate the desired command. For example, my CLOSE button sends a ctrl-K. Each myth command can map up to four different keystrokes (in the Edit Keys tables), so you should be able to retain the functionality of a full keyboard while adding new keystrokes needed for your remote. 

I don't actually use the Asus credit-card remote for day-to-day viewing. My preferred command/control device is an MX-500 unified remote control. It has a learning function, so I can train any button on it (using the various device remote controls)  to do whatever I want: Myth commands, Sony Bravia commands, SA cable box commands, audio receiver commands, etc.

The exit (or go back) button on the keyboard is escape.  So, I tried to program the button into escape, but it said that "backspace" was already assigned.  Does backspace do anything in MythTV?

---

### Post by kyphos on 2010-11-30
> **davidstoll said:**
> The exit (or go back) button on the keyboard is escape.  So, I tried to program the button into escape, but it said that "backspace" was already assigned.  Does backspace do anything in MythTV?

Depends on the context you're in (and on the version of MythTV). I just tried adding backspace as a command on my system. I got a warning telling me that  backspace is already in use for the HISTORYBACK command in the Browser context. I checked, and  it is: on my my system, the HISTORYBACK command has two keymaps: "R" and "Backspace".

I have Myth 0.23.0 (installed from Mythbuntu 10.04). Perhaps you have an older version that doesn't bother to tell you where the conflict is?  Check the keymaps for the Browser context (in the frontend under Setup/Edit Keys) and see if backspace is defined as a command for HISTORYBACK. If it is, you can delete that mapping, and then you should be able to define backspace as the Global ESCAPE command. I'd suggest keeping the existing escape mapping (i.e. add backspace as an additional keymap), so you can continue to use the default mappings on a full keyboard.

---

### Post by davidstoll on 2010-11-30
> **kyphos said:**
> Depends on the context you're in (and on the version of MythTV). I just tried adding backspace as a command on my system. I got a warning telling me that  backspace is already in use for the HISTORYBACK command in the Browser context. I checked, and  it is: on my my system, the HISTORYBACK command has two keymaps: "R" and "Backspace".

I have Myth 0.23.0 (installed from Mythbuntu 10.04). Perhaps you have an older version that doesn't bother to tell you where the conflict is?  Check the keymaps for the Browser context (in the frontend under Setup/Edit Keys) and see if backspace is defined as a command for HISTORYBACK. If it is, you can delete that mapping, and then you should be able to define backspace as the Global ESCAPE command. I'd suggest keeping the existing escape mapping (i.e. add backspace as an additional keymap), so you can continue to use the default mappings on a full keyboard.

I use Mythbuntu 10.10, so I'm up to date.

In Browser, HISTORYBACK has R and Backspace assigned to it.
However, the problem is that BACKSPACE is already assigned in the Global list.  I just deleted that and assigned the backspace button on my remote to the Global ESCAPE..

This works to fix the only button that doesn't work on my new remote...because Streamzap is totally screwed up with 10.10.  Anyway, how do I assign a script (.sh) to a button on a keyboard?  This is less of a Myth question as it is a Linux question.  My remote has 4 colored buttons that I normally have (on my streamzap and other MCE IR remotes) assigned to run scripts.

I'm really disappointed in 10.10 with regards to LIRC and Streamzap.  It is very very frustrating.

Thanks so much for the help!

---

### Post by kyphos on 2010-11-30
I'm new to Linux -  afraid I can't help you with mapping scripts to a keyboard/remote button, but I'm sure there's a way. No doubt one of the Linux experts can shed some light.  Please post back when you find a solution..

---

### Post by davidstoll on 2010-12-01
Starting new thread to figure out key mapping to scripts.

[http://ubuntuforums.org/showthread.php?t=1634946](http://ubuntuforums.org/showthread.php?t=1634946)

---

