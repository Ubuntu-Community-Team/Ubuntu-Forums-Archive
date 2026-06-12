---
title: "Google Chrome and Google Play Movies"
date: 2012-12-18
forum: Multimedia Software
---

### Post by mag1strate on 2012-12-18
Hi Guys,

I want to start watching some of the purchases I have made through Google Play, but the videos use DRM using adobe flash. To circumvent that, you need to install the hal module. 

However, when installed, google chrome will still not play restricted video formats using flash player. I believe it has to do with the fact that it uses the pepper flash player that is integrated with google chrome, but I am not sure. 

Has anyone had any luck getting google play movies to work on google chrome?

Thanks Guys!

---

### Post by tom_say on 2013-01-16
Make sure you have Hal installed and adobe flash plugin 

sudo apt-get install hal 

sudo apt-get install flashplugin-installer 

after this go to chrome://plugins

left side of screen click on the + on details 

disable flash plugin 
/opt/google/chrome/PepperFlash/libpepflashplayer.so

and leave the other enabled 
/usr/lib/flashplugin-installer/libflashplayer.so

there you go chrome should now work with DRM protected files from google play :D

---

### Post by gipbuntu on 2013-04-25
I had this same problem on 12.10, and the previous suggestion worked for me. However, after upgrading to 13.04 today, I now get an error saying: *[COLOR="#0000CD"]There is a problem with your Flash Player. Click here and select "Reset License Files"[/COLOR]*  Nothing happens when I click "here." I tried uninstalling and reinstalling the flashplugin and still broken. I tried both Chrome and Firefox and get the same error. Any ideas or anyone else get the same problem?

---

### Post by gipbuntu on 2013-04-25
I saw that a bug was reported about this [here]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/1168595"), but it doesn't seem to be fixed for me. Will try the suggestions of running a live usb and installing hal to see if it works. I don't want to have to do a fresh install, but I will if necessary.

---

### Post by johnrose13 on 2013-06-08
[ATTACH=CONFIG]243644[/ATTACH]this is what i got after i disabled the said plugin.

---

### Post by Bobby Phoenix on 2013-07-07
> **johnrose13 said:**
> [ATTACH=CONFIG]243644[/ATTACH]this is what i got after i disabled the said plugin.


Go into your exceptions settings for Unsandboxed plug-in access, and make Youtube an exception to allow.  By doing so Chrome is allowed access to the HAL which included with the stand alone system Flash Player that Firefox uses, and is needed to play protected content on Youtube.   This worked for me.


[ATTACH=CONFIG]244493[/ATTACH]

---

### Post by temporos on 2013-11-24
I know, resurrecting an old thread. But this problem persists.

I have the HAL module installed, as well as Adobe Flash. Running Chromium 30.0.1599.114 (Developer Build 30.0.1599.114-0ubuntu0.13.04.2). This is what came with Lubuntu 13.04. I did not change development streams. Still seeing this when I attempt to play movies on Google Play.

[ATTACH=CONFIG]248067[/ATTACH]

Flash Player is 11.2.202.307. I tried to run the ["test" DRM content]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html#id_21709") on Adobe's Flash web site, and it gave me this output.

```
Starts to get video metadata at Sun Nov 24 15:04:55 GMT-0500 2013
Error: Error #3344 [MissingAdobeCPModule] dispatched
Updating AdobeCP module......
AdobeCP module updated. Restarts the play process.
Starts to get video metadata at Sun Nov 24 15:05:03 GMT-0500 2013
DRMContentData received on Sun Nov 24 15:05:04 GMT-0500 2013
authenticationMethod = anonymous
ServerURL = http://drmtest2.adobe.com:8080
license ID = 43345AEF-52FF-3F20-90FF-ABDC98A2E3E4


DRMErrorEvent dispatched by DRMManger received on Sun Nov 24 15:05:09 GMT-0500 2013
event type = drmError
Error Code = 3322 [DeviceBindingFailed]
Sub Error Code = 1107296263
Error Details = 
drmUpdateNeeded = false
systemUpdateNeeded = false

```

I apparently meet all the requirements, but I'm still getting an error 3322 (which indicates no HAL installed). Restarting had no effect. Removing the Flash cache had no effect, either.

```
[COLOR=#333333][FONT=Courier New]cd ~/.adobe/Flash_Player[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]rm -rf NativeCache AssetCache APSPrivateData2[/FONT][/COLOR]
```

---

### Post by temporos on 2014-01-01
I've been abandoned by Google support on this. Please help.

> [FONT=arial]Thanks for contacting Google. [/FONT][COLOR=#333333][FONT=arial]After further investigation, we have confirmed that this is out side of our scope as this is not currently supported, you may want to refer to Ubuntu and Adobe for further help.[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-01-01
hal doesn't work on Chrome. Use Firefox.

Alternatively you can install Windows' flash using pipelight.
[http://fds-team.de/cms/pipelight-installation.html#section_2_3](http://fds-team.de/cms/pipelight-installation.html#section_2_3)
(to switch between Linux flash and piplelight in chrome, go to about://plugins and selectively disable/enable whichever one you choose. In Firefox install galternatives from repo and go to Mozilla-flash plugins, add the path to pipelight flash and you can choose your option. When Linux flash does work (either pepper or the default) it works smoother and there are things that the Wine solution doesn't work so you would want the option to switch)

---

### Post by temporos on 2014-01-01
I've tried both Chromium and Firefox to the same result.

Why doesn't HAL work on Chrome, though? It seems Chromium (which is the default browser in Lubuntu) is becoming incompatible with more and more things online, including Google products.

---

### Post by nigelkeen1971 on 2014-02-26
> **temporos said:**
> I've tried both Chromium and Firefox to the same result.

Why doesn't HAL work on Chrome, though? It seems Chromium (which is the default browser in Lubuntu) is becoming incompatible with more and more things online, including Google products.

On Chrome 33, this is not a HAL issue it is a Flash Plugin issue, I have managed to get Chrome to play Google Play films by:

To go:

chrome://plugins

Disable Adobe Flash Player

Enable [COLOR=#000000][FONT=Ubuntu]**IcedTea-Web Plugin (using IcedTea-Web 1.2.3 (1.2.3-0ubuntu0.12.04.3))**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]- Version: 1.2.3[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]
(If you haven't got IcedTea Web Plug you can download it from the software centre)

[/FONT][/COLOR]

---

