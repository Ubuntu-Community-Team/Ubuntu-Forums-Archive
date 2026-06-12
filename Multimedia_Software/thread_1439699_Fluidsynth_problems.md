---
title: "Fluidsynth problems"
date: 2010-03-26
forum: Multimedia Software
---

### Post by Tootler on 2010-03-26
I use fluidsynth for midi playback from a music notation editor. I had it working fine in Intrepid, but have run into some problems when I upgraded to Jaunty.

Before upgrade, I used to start fluidsynth when I needed it using the qsynth gui which I could then dismiss leaving fluidsynth running in the background ready for use.

Since upgrading, I found that qsynth starts up on ubuntu startup. This would not be a problem except it interferes with my printer software (HPLIP toolbox). On startup, I get a message from HPLIP to the effect "cannot find the system tray, shutting down" and it fails to startup. If I remove qsynth, then the printer toolbox starts up OK.

I tried starting fluidsynth from the terminal, and that worked OK except that you can't dismiss the terminal or it will shut down fluidsynth. 

I would like to either;

Prevent qsynth from starting on ubuntu startup so that I can start it when I need it as used to happen with Intrepid (*preferred*)

or

Be able to start fluidsynth from the terminal and then dismiss the terminal while leaving fluidsynth running in the background. (I could then write a simple shell script to do this)

I would like to get this sorted now as I wish to upgrade again, but need to know how to deal with any problems like this if they arise again.

Geoff

---

### Post by Tootler on 2010-03-27
Bump

---

### Post by Tootler on 2010-06-18
I'm still having this problem 3 months later. I cannot find any obvious way of ensuring that Qsynth does **not** load on startup. Any suggestions appreciated.

Geoff

---

### Post by cchhrriiss121212 on 2010-06-18
Odd that qsynth starts when you boot, did you set it to do that? Anyhow, you can set what applictions run at boot by going to Preferences>Startup Applications.
You could also create a custom launcher for fluidsynth by right clicking on the top panel and following instructions. Or you could open it with a keyboard shortcut.

---

### Post by Tootler on 2010-06-18
> **cchhrriiss121212 said:**
> Odd that qsynth starts when you boot, did you set it to do that? Anyhow, you can set what applictions run at boot by going to Preferences>Startup Applications.

I did not consciously set it up to start on boot. I simply installed from the terminal using "sudo apt-get qsynth" I could try uninstalling and using synaptic, but that should not make any difference.

I had already checked the startup apps before I posted. Qusynth was not there or I would have disabled it.


> You could also create a custom launcher for fluidsynth by right clicking on the top panel and following instructions. Or you could open it with a keyboard shortcut.

I hadn't thought of that. I have a shell script for fluidsynth. I'll give it a try.

Cheers

Geoff

---

### Post by Tootler on 2010-07-02
I think I have it. Alt+F2 then run the shell script seems to work OK

I had some problems on upgrading to 10.04 which took a bit of sorting but once I had those sorted then I was able to try that. It seemed to work OK.

Thanks for suggestions, though the Qsynth issue has not been resolved running the shell script is fine. I can just run it when I need it.

Geoff

---

