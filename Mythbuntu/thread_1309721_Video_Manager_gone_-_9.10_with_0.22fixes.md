---
title: "Video Manager gone - 9.10 with 0.22fixes"
date: 2009-11-01
forum: Mythbuntu
---

### Post by neutron68 on 2009-11-01
I performed a successful update from Mythbuntu 9.04 to 9.10.  Today, I was going to try and play back some videos that are in the VIDEOS directory on the machine, and there is no way to select and play them.  Then, I started looking for the Video Manager settings so I could scan the directory and get a playback list of the videos, and there is NO Video Manager menu item ANYWHERE.  

Is this an expected thing with Mythbuntu 9.10 and myth 0.22?

Eric

---

### Post by joshoekstra on 2009-11-01
Yup, press M in the mythvideo screen, that's where your options are :)
Might need to change location, here it changed to default...

---

### Post by iamlindoro on 2009-11-01
[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

---

### Post by neutron68 on 2009-11-01
AH!  Thank you.

I see from the Myth Video 0.22 Transition Guide, that the Video Manager has been deprecated.

OK.  Now, I'm looking for Myth Video, so I can follow the directions in the Myth Video 0.22 Transition Guide.  
I don't see any menus in Mythtv that have a Myth Video choice.  Where is it?

Eric

---

### Post by tgm4883 on 2009-11-01
> **neutron68 said:**
> AH!  Thank you.

I see from the Myth Video 0.22 Transition Guide, that the Video Manager has been deprecated.

OK.  Now, I'm looking for Myth Video, so I can follow the directions in the Myth Video 0.22 Transition Guide.  
I don't see any menus in Mythtv that have a Myth Video choice.  Where is it?

Eric

Media Library > Watch videos

---

### Post by neutron68 on 2009-11-01
Thank you!

Myth Video = Watch Videos

---

### Post by nickrout on 2009-11-02
> **neutron68 said:**
> Thank you!

Myth Video = Watch Videos

same as 0.21 :)

---

### Post by chipppy on 2009-11-02
dont forget that press 'm' = menu sometimes for more options.
Also along that note press 'i' for more info.

---

### Post by neutron68 on 2009-11-02
I'm trying to follow the Myth Video .22 Transition Guide, and many of the related menu options it mentions are missing on my system!!

For example, I don't have the following menu items:
- no Setup > Media Settings > Video Settings option
- no Scan For Changes option, when you bring up the MENU with the M-key

Does that indicate a failed upgrade or bugs in the 0.22 code?

Eric

---

### Post by tgm4883 on 2009-11-02
> **neutron68 said:**
> I'm trying to follow the Myth Video .22 Transition Guide, and many of the related menu options it mentions are missing on my system!!

For example, I don't have the following menu items:
- no Setup > Media Settings > Video Settings option
- no Scan For Changes option, when you bring up the MENU with the M-key

Does that indicate a failed upgrade or bugs in the 0.22 code?

Eric

You have MythVideo installed?

Any errors in your frontend logs?

---

### Post by neutron68 on 2009-11-02
> **tgm4883 said:**
> You have MythVideo installed?

Any errors in your frontend logs?
I just went into the Mythbuntu Control Center and Myth Video was NOT checked.  I thought it would have been installed by default??  No?

OK. Now Myth Video is installed.  
Now, I have the Setup > Media Settings > Video Settings option.
I have the /var/lib/mythtv/video folder set up as the videos folder in the Storage Group screen of the mythtv-setup.
I still don't get the Scan for Changes choice with I hit the M key.

The only error I see in the mythtvfrontend log looks unrelated to me:
```
2009-11-01 18:53:34.012 MythXOpenDisplay() failed
2009-11-01 18:53:34.012 ScreenSaverX11Private, Error: Failed to open connection to X11 server
2009-11-01 18:53:34.012 DPMS is not supported.
mythfrontend.real: Fatal IO error: client killed
```

---

### Post by neutron68 on 2009-11-02
No, wait.  After restarting all the Mythtv programs, I now get the Watch Videos choice under the Media Library menu choice.  And, the Scan For Changes message is available with a press of the M key.

Mystery solved, it would seem?

Thanks for the diagnostic questions.

Eric

---

### Post by tgm4883 on 2009-11-02
> **neutron68 said:**
> No, wait.  After restarting all the Mythtv programs, I now get the Watch Videos choice under the Media Library menu choice.  And, the Scan For Changes message is available with a press of the M key.

Mystery solved, it would seem?

Thanks for the diagnostic questions.

Eric

Yep, mystery solved

---

### Post by usererror on 2009-11-25
Another case of RTFM on my part.  BUT I was also confused as the original poster was.

In my case my menu style was still set to "classic" under Setup > Appearence.  I set it to Default and read her to press "M" to scan for directory changes and vwalla everything works like a charm.

However, perhaps I still need to read the manual, but where the hell did they move the "scan imdb" option?

I see they are using a new site for movie DB information but I can't find how to download the new data for the life of me.

---

### Post by nickrout on 2009-11-26
w

---

### Post by usererror on 2009-11-26
> **nickrout said:**
> w

Yup, it was the W key, after some more digging on that Transition page at the myth wiki i was enlightened!

---

