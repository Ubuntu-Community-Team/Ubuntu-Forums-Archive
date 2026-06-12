---
title: "Need Help Configuring Sierra 598u Wireless Modem in CrunchEee(OpenBox)"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by clinto on 2010-04-15
I'm trying to set up CrunchEee 8.10.02(Ubuntu based using OpenBox wm) on my boss' Eee PC 900 and she uses a Sprint 598u USB modem.  I've found a guide from sprint, but it has you using Kppp, which doesn't work in OpenBox.  I'm using gnome-ppp instead.

Sprint guide: [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

The Sprint guide has me do these things first:
1. Boot with modem unplugged.
2. Command: sudo modprobe -r usbserial
3. Command: sudo modprobe vendor=0x1199 product=0x0025
4. Make sure you have a working connection with internet.
5. Install KPPP and KPPLogview.

Since KPPP doesn't work in OpenBox, I downloaded gnome-ppp instead.  I'm very much an amateur with networking altogether, and I've never really messed with these usb modems.  The differences between Kppp and gnome-ppp are enough to leave me a bit confused.  I've tried my best to guess using what information I could gather from the guide, but it's still not connecting.

I'll put the differences in a code box:
```

Sprint guide to set up Kppp:
- Set connection name.
- Add #777 to "phone number".
- Add modem name.
- Set "modem device" as "/dev/ttyUSB0".
- Set "flow control" as "Hardware [CRTSCTS]".
- Set "line termination" as "CR".
- Set "connection speed" as "921600".
- Set "use lock file" on.
- Set "modem timeout" to 60 seconds.
- Verify Kppp can communicate with wireless modem by clicking "query modem" which should return a multi-line response.
- Set pppd version to "2.4.4"
- Set pppd timeout to "30 seconds".
- Set "show clock on caption" to on.
- Set "disconnect on x server shutdown" to on.
- Save configuration.

Differences between Kppp and gnome-ppp:
- Gnome-ppp doesn't provide field for entering connection name.
- Along with setting phone numbers, there is an option in gnome-ppp for setting Init Strings(which I'm uncertain about, it's currently set to "Init 2: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0".
- Gnome-ppp doesn't provide a field for entering modem name.
- No options in gnome-ppp for "flow control", "line termination", "use lock file", or "modem timeout".
- Connection speed in gnome-ppp only provides a drop down list with options up to 460800, as opposed to the 921600 speed that Kppp should be set to.
- No option in gnome-ppp for querying the modem, pppd version, pppd timeout, "show clock on caption", or "disconnect on x server shutdown".
- Gnome-ppp provides some options Kppp doesn't, including: 
- "Phone line(tone or pulse)" - set to tone
- "Dial prefix" field - empty
- "Dial attempts" number selector - set to 1
- "wait for dialtone" checkbox- checked
- IP selector(dynamic or static with address field) - dynamic selected
- DNS selector(automatic or manual) with domain name field - dynamic selected with domain name field blank
- on connection(minimize or dock in notification area) - set to dock
- "auto reconnect" checkbox - checked
- "Abort connecting if line is busy" checkbox - unchecked
- "Abort connecting if no dialtone" checkbox - checked 
- "Check carrier line" checkbox - checked
- "check default route" checkbox - checked
- "Ignore terminal strings(stupid mode)" checkbox - unchecked
- "Send custom reply" checkbox with field - unchecked
- "Idle time" selector - disabled

```

I've read that the modem doesn't use username or password but something is needed to prevent errors, so I've entered "user" for both username and password.  In the Phone Number box I put #777.  Hit connect and it either sits there saying it's dialing, or it says it can not open modem.

I would also like to know how to set linux up to set these values at boot instead of entering them by hand each time(since my boss doesn't know anything other than point-and-click, and it's a bit tedious anyways).  I'm sure there is a config file that executes commands at boot or something.  Can anyone point me in the right direction?

---

### Post by snowpine on 2010-04-15
You aren't going to like my advice. :) Don't waste your time with Cruncheee 8.10; it was a very cool distro for its time (I enjoyed using it until 9.04 was released), but 8.10 is reaching "end of life" in 2 weeks and will no longer be supported. 

I cannot recommend a specific distro (since I am not familiar with the Sierra modem) but definitely use something that is currently supported (9.10 or newer, if you want to stick with the Ubuntu family, otherwise there are hundreds of choices). Once a distro reaches "end of life" it receives no security patches, no bug fixes, you cannot install applications from the repositories, you cannot upgrade to a new release, and you are on your own if something breaks. :(

ps Why do you say kppp won't work in Openbox?

---

### Post by snowpine on 2010-04-15
I just checked the CrunchBang forums for you and found this thread, hope it helps! :)

[http://crunchbanglinux.org/forums/topic/775/howto-set-up-sprint-evdo-usb-modem-on-crunchbang/](http://crunchbanglinux.org/forums/topic/775/howto-set-up-sprint-evdo-usb-modem-on-crunchbang/)

---

### Post by clinto on 2010-04-15
> **snowpine said:**
> I just checked the CrunchBang forums for you and found this thread, hope it helps! :)

[http://crunchbanglinux.org/forums/topic/775/howto-set-up-sprint-evdo-usb-modem-on-crunchbang/](http://crunchbanglinux.org/forums/topic/775/howto-set-up-sprint-evdo-usb-modem-on-crunchbang/)

Wow... I just shutdown and was going to install Ubuntu Netbook Remix... hmm... I'll try that just to see if it works.  I'm thinking UNR may be better for the person I'm installing this for anyways, since she would have to do her own upgrading and such...

---

