---
title: "Skype white noise problem"
date: 2009-09-23
forum: Multimedia Software
---

### Post by ceeborus on 2009-09-23
Hi I'm complete  Ubuntu newbie  and I would really appreciate if sombody could help me with the issue.


The problem:

A loud white noise appears during some of Skype conversations. It blocks completely my voice  to a callee. The Skype conversation is always ok during a call untill it is disrupted and the call disconnected  (usually due to a low quality of internet connection) The noise appears ALWAYS after reestablishing a conversation.


Attempts to fix it:

A temporary solution is to log-out the Ubuntu session and log-in again. Unfortunately it works only until the first disconnection.  I've searched forums but didn't find a right solution. For some people worked changing Skype settings to these:

Sound In:  **HDA NVidia (hw:NVidia,0)**
 Sound Out: **pulse**
 Ringing:   **pulse**

Unfortunately I can't change Skype sound settings for any different than "PulseAudio server (local)" for any of the three options so the solution provided is not possible for me.



Gear:

Cam: Logitech Pro9000 (with a built-in microphone)
Headset:  Logitech PC headset 860

OS:
Ubuntu 9.04
Skype version: 2.1.0.47 (beta)

Thank you in advance for any ideas that you wish to share with me. :)

---

### Post by mionescu on 2009-09-23
Since your version of Skype is the new beta version, your problem might be related with the one describred at
[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)
(the second question, about clicking noise).

If the fix describred there doesn't work for you, my advice is to install the stable version (2.0) of Skype using medibuntu. That's what I did to solve the noise problem.

---

### Post by ceeborus on 2009-09-23
Cheers for the answer. The solution from skype website unfortunately didn't work for me but I managed to install the older version of skype and there is no white noise now.  Now there is another problem - my voice is not recorded by Skype. Tried different settings (now unblocked) but Skype Echo (test call service)  does not play my voice. Any tips what 2 do? Thanks again. :)

---

### Post by akber on 2009-09-29
I have the same problem, sometimes when I call people its just white noise (according to them), and sometimes its fine. I also have to log out or restart to fix the problem. Also when i call the skype call testing service I will just get the blaring white noise in return, but sometimes it works just fine. Really need a fix for this little peeve.

---

### Post by Turtle.net on 2009-10-10
> **ceeborus said:**
> Cheers for the answer. The solution from skype website unfortunately didn't work for me but I managed to install the older version of skype and there is no white noise now.  Now there is another problem - my voice is not recorded by Skype. Tried different settings (now unblocked) but Skype Echo (test call service)  does not play my voice. Any tips what 2 do? Thanks again. :)
In skype 2.0 I had to try all the different options for Sound In. Pulse doesn't work.
On my installation it's Hw 2 that need to be on Sound In, and pulse for the rest.

---

### Post by ceeborus on 2009-10-10
The solution has been found. Its name is [COLOR=#000000][FONT=AlArabiya][http://www.skype.com/go/getskype-linux-beta-static ]("http://www.skype.com/go/getskype-linux-beta-static")
Download, unzip and simply run without any need for installations. Works just fine for me.
[/FONT][/COLOR]

---

### Post by svaens on 2009-10-12
I would call this NOT SOLVED to me. 

I still get the same static, white noise (very loud) problem with this static version. 

With the tip provided by 'n5pwp_tux' on the skype forums
[http://forum.skype.com/index.php?showtopic=411431&st=80&p=1968371&#entry1968371](http://forum.skype.com/index.php?showtopic=411431&st=80&p=1968371&#entry1968371)

that is, after killing pulseaudio, and restarting it with the -vv option (i have yet to read-up what the option is for)

```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

Then re-adjusting the volume levels again (because they might be askew since the last problems)

and then restarting skype, seems, so far, to fix the problem. After that, I was able to use skype, the regular beta download (non the static archive). I imagine i'd be able to use the static version too.

Will do more tests later.

---

### Post by Turtle.net on 2009-10-16
I read [this]("http://share.skype.com/sites/linux/"), and i tried some little things. i installed the pulseaudio tools :
```
sudo apt-get install padevchooser paman paprefs pavucontrol pavumeter
```
then I played a little bit with Applications->Sound&Video->Pulseaudio Device Chooser and Volume Control to make sure that everything was set up correctly.
Then I disable in Skype the option "Allow Skype to automatically adjust my mixer levels" and the blank noise disappeared ....

---

