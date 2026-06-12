---
title: "HTC Hero as modem"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by evillan on 2009-08-14
Does anybody have experience with HTC Hero as a modem on ubuntu 9.04?
Does it work out of the box, do you have to tinker with it, or doesn't it work at all?

---

### Post by user256 on 2009-08-14
While i can't speak to the HTC Hero, The HTC Dream can be used as a wifi tether, however it required rooting first, you're best bet would probably be to check out the wonderful XDA [http://forum.xda-developers.com/forumdisplay.php?f=508](http://forum.xda-developers.com/forumdisplay.php?f=508) They have a thread specific to tethering [http://forum.xda-developers.com/showthread.php?t=546066&highlight=tether](http://forum.xda-developers.com/showthread.php?t=546066&highlight=tether)

I've had so much fun playing around with my android, also gotta love banshee - it lets you use the dream not unlike an ipod! Not sure how it responds to the Hero though!

Good luck!

---

### Post by kaivalagi on 2009-08-18
> **user256 said:**
> While i can't speak to the HTC Hero, The HTC Dream can be used as a wifi tether, however it required rooting first, you're best bet would probably be to check out the wonderful XDA [http://forum.xda-developers.com/forumdisplay.php?f=508](http://forum.xda-developers.com/forumdisplay.php?f=508) They have a thread specific to tethering [http://forum.xda-developers.com/showthread.php?t=546066&highlight=tether](http://forum.xda-developers.com/showthread.php?t=546066&highlight=tether)

I've had so much fun playing around with my android, also gotta love banshee - it lets you use the dream not unlike an ipod! Not sure how it responds to the Hero though!

Good luck!

The Hero turns up in Banshee as you described :)

There is a tetherbot app on the market place, I haven't tried it yet but it provides an interface to the settings for tethering...

Side note: I've created a python script to create android compatible video, new thread for it here: [http://ubuntuforums.org/showthread.php?p=7805696](http://ubuntuforums.org/showthread.php?p=7805696)

---

### Post by user256 on 2009-08-19
> **kaivalagi said:**
> Side note: I've created a python script to create android compatible video, new thread for it here: [http://ubuntuforums.org/showthread.php?p=7805696](http://ubuntuforums.org/showthread.php?p=7805696)

You just became my new best friend!! Love it thanks!

---

### Post by chris v. on 2009-08-22
Unlike the other android phones, the Hero has builtin tethering capabilities (via GPRS/UMTS), so you do not need a special app and/or a rooted phone. This is at least true for unbranded phones, in a branded phone sold with a contract this may be disabled, though.

To enable GPRS/UMTS tethering, just connect the phone with USB, go to "settings"->"wireless" in the menu and set the checkbox on the last item (should read like "enable internet sharing" or similar, can't tell the exact words because i have a german phone, there it says "Mobile Netzwerkfreigabe").

On the notebook, there was no additional configuration necessary, the new connection was automatically detected and used (Ubuntu 9.04 with current patches).

---

### Post by MeanEYE on 2009-08-31
> **evillan said:**
> Does anybody have experience with HTC Hero as a modem on ubuntu 9.04?
Does it work out of the box, do you have to tinker with it, or doesn't it work at all?

Yes it works out of the box... On your phone, go to Settings -> Wireless Controls and turn on Mobile network sharing.

Your phone will automatically recognized as LAN. On your computer left click on network manager and select Auto usb0 (or eth1 whatever name it has).

That's it... It works like a charm :) no additional apps needed ;)

---

### Post by kaivalagi on 2009-09-17
> **chris v. said:**
> Unlike the other android phones, the Hero has builtin tethering capabilities (via GPRS/UMTS), so you do not need a special app and/or a rooted phone. This is at least true for unbranded phones, in a branded phone sold with a contract this may be disabled, though.

To enable GPRS/UMTS tethering, just connect the phone with USB, go to "settings"->"wireless" in the menu and set the checkbox on the last item (should read like "enable internet sharing" or similar, can't tell the exact words because i have a german phone, there it says "Mobile Netzwerkfreigabe").

On the notebook, there was no additional configuration necessary, the new connection was automatically detected and used (Ubuntu 9.04 with current patches).

Thanks :popcorn:

Waiting for that HTC Sense UI update....the phone really needs it...

edit: The option is greyed out for me, the phone is unbranded but using a vodafone sim...do I need mobile internet with my provider first - I was assuming I could also use this to connect through to a wifi network from an "un-wi-fi'ed" PC...effectively using the phone as a wi-fi adapter

---

### Post by getut on 2009-12-26
> **MeanEYE said:**
> Yes it works out of the box... On your phone, go to Settings -> Wireless Controls and turn on Mobile network sharing.

Your phone will automatically recognized as LAN. On your computer left click on network manager and select Auto usb0 (or eth1 whatever name it has).

That's it... It works like a charm :) no additional apps needed ;)

Have you actually got this working? I have the Sprint version and am having problems.

Mine shows up as USB0 just like yours, but the minute I try to use the data connection, the phone shows the error message 67 can't connect for bad username and password.

It appears like I need the USB0 to show up in the "Mobile Broadband" tab instead of wired network so that I can enter the #777 for dial number. I'll post back with the exact error message.

---

### Post by getut on 2009-12-26
```
Data call failure.

Error Code 67. Registration failure. Press [OK] for Options. Your PCS Vision username and/or password may be incorrect. Please try again.
```

I can use the data network from the phone itself, so that isn't the problem. Please help.

---

### Post by GeorgeVita on 2009-12-27
Hi **getut**,
although I cannot test it, I thing you have to setup all parameters needed (APN, username, password, phone#) on network manager 'mobile broadband connection'. The phone will be just the 'remote' modem. You can connect using the phone's application because it is already configured.

Regards,
George

---

### Post by getut on 2009-12-30
> **GeorgeVita said:**
> Hi **getut**,
although I cannot test it, I thing you have to setup all parameters needed (APN, username, password, phone#) on network manager 'mobile broadband connection'. The phone will be just the 'remote' modem. You can connect using the phone's application because it is already configured.

Still no luck with this... no matter how much information I give network managers mobile broadband configuration, the hero still shows up as USB0 under the wired network configuration in network manager.

Because it is showing up as a wired network, I speculate that it is not sending the #777 like it would if it showed up in mobile broadband and is therefore giving the error message I listed above.

Please help me.

---

### Post by kaivalagi on 2009-12-30
I'm assuming you get these errors because you are trying to use the phone as a true modem? :
```

ata call failure.

Error Code 67. Registration failure. Press [OK] for Options. Your PCS Vision username and/or password may be incorrect. Please try again.

```

Do you need to use your phone as a modem per say?

Do you have mobile internet with the phone, can that be used for your internet connection? If you do and can then it should be as simple as this:

[LIST=1]
[*]Plugin your phone to your PC USB
[*]On the Android phone goto Menu->Settings
[*]The onto Wireless Controls section and first check "Mobile Internet" then check "Mobile Network Sharing"
[*]You should then be able to use the phone via USB as a wired network connection...
[/LIST]

Hope that helps

Apologies if I have already spelled out what you have done, but I am sure it worked for me in the past in Ubuntu without issue. I am running Arch now and haven't tried it as yet...

---

### Post by getut on 2009-12-30
> **kaivalagi said:**
> I'm assuming you get these errors because you are trying to use the phone as a true modem? :
```

ata call failure.

Error Code 67. Registration failure. Press [OK] for Options. Your PCS Vision username and/or password may be incorrect. Please try again.

```

Do you need to use your phone as a modem per say?

Do you have mobile internet with the phone, can that be used for your internet connection? If you do and can then it should be as simple as this:

[LIST=1]
[*]Plugin your phone to your PC USB
[*]On the Android phone goto Menu->Settings
[*]The onto Wireless Controls section and first check "Mobile Internet" then check "Mobile Network Sharing"
[*]You should then be able to use the phone via USB as a wired network connection...
[/LIST]

Hope that helps

Apologies if I have already spelled out what you have done, but I am sure it worked for me in the past in Ubuntu without issue. I am running Arch now and haven't tried it as yet...

Actually your steps above are EXACTLY what I do, but then any action that I take that tries to use the network causes the error I posted to pop up. If I use the internet from the phone itself it works fine with no error.

That is what led me to believe that the PC should be responsible for sending the #777 and such but my entire premise may be off if what you are saying is true.

It seems like if Ubuntu uses it as a wired connection, then the phone should be responsible for signing on to the Sprint network and it would b e a phone problem. If the PC should be responsible for signing on the sprint network then it is an ubuntu problem.

I just tried it again and same error.

I'm actually hoping this will be a resolvable Ubuntu problem. If its a phone problem, Sprint is going to give me a hell of a time when I reproduce the problem and tell them I'm using linux. They'll swear up and down its a linux problem and there is nothing they can do.

---

### Post by archer007 on 2009-12-30
Having this exact same problem. Is there a fix for this?

---

### Post by getut on 2009-12-31
> **archer007 said:**
> Having this exact same problem. Is there a fix for this?

Well.. good news... kind of. I just replicated the issue on a windows laptop. At least I will be able to call now and not have them stop helping me with the problem just because I am using an unsupported OS.

I'll still call and START the tech support call and tell them I'm using linux so at least it will go on the record that people are using it and help towards getting it officially supported. When they balk at helping me with it at all, then I'll mention... Oh yea... I can replicate this issue in Winblows.

I'll post with the results. If it is a carrier side fix it won't help to post it here.. but if it is a hidden phone setting it will help other people greatly.

---

### Post by getut on 2009-12-31
Ok... right from the keyboard of Sprint tech support.

"Sprint chose to block this service beginning 2/1/06, for all customers that do not have a Phone as Modem Plan. This transition has taken some time and is not a policy change; it is an enhancement to the technology reinforcing the policy."

So they are artificially crippling the phone so they can sell the feature back to you.

Looks like I'll be rooting the phone today so I can use [this.]("http://code.google.com/p/android-wifi-tether/")

I'll update again with how this goes.

---

### Post by getut on 2010-01-04
Ok.. I didn't have to root the phone and I also didn't have to buy any software.

Sprint is blocking tethering on the phone side but here is the procedure to get USB tethering to work on a Sprint HTC Hero that is blocked.

1) Go to settings/wireless controls and turn off BOTH mobile network AND mobile network sharing.
2) Go into mobile network settings/Mode of Operation and set it to 1X-Only.
3) Connect your USB cable to your phone and Ubuntu machine
4) Start the PHONES web browser and wait for the error message about needing the network.
5) Go back to settings/wireless controls and then turn on mobile network and then as quickly as possible after mobile network sharing gets ungrayed, click it to enable mobile network sharing.
6) You should now be connected and able to browse on the tethered machine, but you are at 1x speed. Go back in and set mode of operation back to hybrid and you'll have full speed.

Evidently this takes advantage of a bug in the blocking procedure Sprint uses.

---

### Post by kaivalagi on 2010-01-04
That's just plain annoying, sorry to hear it is a legitimate block rather than an issue per say.

You could always try backing up and putting a custom ROM on it instead? You would lose the nice Sense UI though :(

I use the HTC Hero (pre sprint version for UK), I guess that the ROM image for it will not install on your phone? Not a GSM? It is available from the HTC site...just a thought and probably not worth a shot...

---

### Post by Chiapo on 2010-01-20
Not sure how to get the info from your particular device, but the following APN information works for some tethering on Cellular South:

Username = sip# it looks like a [email]phonenumber@cs3g.com[/email]  

Password = hex esn IN ALL CAPS  

Phone number to dial = #777

I haven't tried this myself, my phone was much more simple!

Good luck!

---

### Post by thefrozenpenguin on 2010-06-27
Just for info my girlfriend has a Hero on an Orange UK Monthly contract and the above "Network Sharing" works a treat.

Thanks everyone. :)

---

### Post by thefrozenpenguin on 2010-06-27
Just for info my girlfriend has a Hero on an Orange UK Monthly contract and the above "Network Sharing" works a treat.

Thanks everyone. :)

---

