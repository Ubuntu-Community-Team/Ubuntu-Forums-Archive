---
title: "no mic on chrome &amp; firefox, works great on skype"
date: 2013-02-25
forum: Multimedia Software
---

### Post by al.adab on 2013-02-25
hello,

for the past three or four days, the microphone on both chrome and firefox has stopped working. It's impossible to record or make phone calls. On the other hand, it works great on skype. 

I'm on xubuntu 12.04 and still have the original sound settings - any idea of what's going on? I checked on various Google forums, and came across people who have similar issues on Windows, though couldn't find any ref. to Linux. 

Can you plz help? thanks

---

### Post by al.adab on 2013-02-25
sorry I've forgotten: I'm using an IBM Thinkpad T42, if that's relevant and my internet connection is all right.

---

### Post by al.adab on 2013-02-26
OK, here's what I've just done - if it helps narrowing it down a bit at all: 

- launched Pulse Audio>sound settings>input devices (which shows a "Alsa Chrome plugin" at "Playback); 
- opened [https://support.google.com/chrome/bin/answer.py?hl=en-GB&answer=1407892;](https://support.google.com/chrome/bin/answer.py?hl=en-GB&answer=1407892;) 
- launched [http://vox.io](http://vox.io) > Test Call; 
- launched Skype>Test Call.

Result: 
a) clicking on the chrome microphone icon and/or making a test call on vox.io produced no result: input devices registers no signals;
b) Skype test call: input and output signal is loud and clear.

any idea?

---

### Post by xc3RnbFO8P on 2013-02-26
Maybe re-install Google Talk Plugin
[http://www.google.com/talk/]("http://www.google.com/talk/")

---

### Post by al.adab on 2013-02-28
just re-installed + upgraded the google plugin. No positive outcome: still no sound....

---

### Post by al.adab on 2013-03-02
bump? :)

---

### Post by dsiegel3 on 2013-03-04
Skype's not working for me -- no microphone input, though the mike works with Sound Recorder.

In the process of testing Skype fixes, I disabled microphone support for Google Voice on Firefox.  I had to go into Google gmail settings and 
reset Voice and video chat device configuration (under the Chat tab).

Did you have to do anything to get Skype working?

---

### Post by al.adab on 2013-03-05
I disabled "enable echo cancellation (recommended)" on gmail>settings>chat and the mic now responds...

mic also works with sound recorder, for some reason (totally unrelated to the option above, though. 

i didn't have to do anything to get skype working, sorry cannot be of help here...

---

