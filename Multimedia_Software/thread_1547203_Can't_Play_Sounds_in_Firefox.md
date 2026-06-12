---
title: "Can't Play Sounds in Firefox"
date: 2010-08-06
forum: Multimedia Software
---

### Post by baneberry on 2010-08-06
When I attempt to use a Firefox Addon like Simple Timer, the audio alarm will not work.  Instead, I get an error message 

[COLOR="DarkOrange"]Could not play the audio file!  NS_ERROR_FAILURE[/COLOR]

I can get the same sounds to play in Google Chrome, but I prefer Firefox.  

Any ideas on how to fix?

---

### Post by lovinglinux on 2010-08-06
> **baneberry said:**
> When I attempt to use a Firefox Addon like Simple Timer, the audio alarm will not work.  Instead, I get an error message 

[COLOR="DarkOrange"]Could not play the audio file!  NS_ERROR_FAILURE[/COLOR]

I can get the same sounds to play in Google Chrome, but I prefer Firefox.  

Any ideas on how to fix?

Go to the extension preferences and test the audio alarm there. Can your hear the default sound? Can you hear when you choose a custom file?

You cannot compare it with Chrome, since this sound is provided by an extension API, which does not exist on Chrome.

---

### Post by baneberry on 2010-08-06
I get the same message with the default alarm:
[COLOR="DarkOrange"]
Simple Timer: Could not play the audio file!
NS_ERROR_FAILURE[/COLOR]

The same thing happens with Tea Timer, so it's not an error with the extension.

---

### Post by lovinglinux on 2010-08-06
> **baneberry said:**
> I get the same message with the default alarm:
[COLOR="DarkOrange"]
Simple Timer: Could not play the audio file!
NS_ERROR_FAILURE[/COLOR]

The same thing happens with Tea Timer, so it's not an error with the extension.

Create a new profile just to see if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

