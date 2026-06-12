---
title: "audacity to record voice"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by vincentvee on 2007-05-02
i'm trying to record voice for a presentation voice over, basically so i can host my training program online, having trouble doing this with audacity, i think i am using thee right thing, but maybe someone can tell me otherwise and point me to another app for recording

---

### Post by imdidactic on 2007-05-03
I use Audacity as well.  You probably need to check the configuration on your input device, but you can also try Ardour.  It's the program that most people are switching over to now.

---

### Post by ratbagradio on 2007-05-03
Review your install. And then go to the top right of your Ubuntu screen and click on the audio  icon. Check your settings.

-- then check System/Sound Preferences in Ubuntu 

Inside Audacity make sure you have :

(a) configured the microphone volume  correctly by moving the pointer up or along.

(b) then review the drop down panel where you can select various sound inputs. Speak into your microphone with the sound button down to see what each of these inputs give you. When you gets waves, you've got sound being recorded. It wiull work in at elast tow of these options.

(c) finally, check your mic. Does it work? Is it a pc mic? Does it need preamp to work...etc

---

### Post by leodp on 2007-05-04
Have you enabled mic capture? Go to any mixer, like kmix on kubuntu, or alsamixer (go to capture with the tab key)  and switch it on.
Is mic boost also on?

You can do a quick test with 
rec test.wav
This command will start recording th the file test.wav (strange, isn't it?)
If no audio has been recorded, or the program freezes, maybe you have to change the mixer settings again.
When it's ok, then most probably also audacity and the like will work.

Ciao, Leo

---

