---
title: "skype (not connecting to pulseaudio in Ubuntu 10.04)"
date: 2010-09-26
forum: Multimedia Software
---

### Post by skoledin on 2010-09-26
I think I've done a pretty thorough search and haven't found a match to my issue, but please just point me in right direction if I've missed something.

Just upgraded to Lucid (32bit), pulse generally seems to work ok: I get sound out,  I can see various apps connecting via the Sound Preferences dialog (audacious, flash via alsa interface, etc.), and my mic seems to work fine too.

However, when starting skype (v2.1.0.81 which defaults to pulseaudio if it's running), it isn't able to output any sound and I never see a connection appear in Sound Preferences. Don't really want to force it to use Alsa or anything like that; I'd be fine with pulse if it would just work.

I've tried installing the .deb from the skype site as well as the official ubuntu package, with the same result. Any idea why pulse seems to be working, but skype can't seem to use it properly?

Thanks for any help with this.

---

### Post by dirghrabadia on 2010-09-26
Make sure you have all your sound devices (speakers,mic,ringing) selected to PulseAudio Server (local). Thats what I have got and it works for me :)

---

### Post by kostkon on 2010-09-26
Hmm, strange. Maybe it's sending its audio to another device; do you have more than one audio devices?

You could install the *PulseAudio Volume Control* utility in order to try to send Skype's audio (output and ringing) to your default audio device (you need to make a call in order to see it appearing in the Application tab of the volume control utility).

Also, check in SKype's preferences if the PulseAudio Server is selected as input, output and ringing device (you never know, although, it should be the only available option); and, better uncheck the *Let Skype adjust my sound device settings* option.

---

### Post by skoledin on 2010-09-26
Doh. Thanks for the quick replies, but it looks like I finally figured our what my issue was. Here are the details in case anyone else has the same situation.

It turns out that Skype actually was showing up as a Client under PulseAudio Manager. It still doesn't appear as a separate application in Sound Preferences, but it looks like that's because it plays via "System Sounds".  I generally keep System Sounds muted and therefore wasn't getting any output from Skype.

To correct, simply go to the PulseAudio Volume Control and make sure System Sounds is turned up, or equivalently, under System->Preferences->Sound make sure Alert volume under the Sound Effects tab is at a non-zero level.

Thanks for the tips, but in the end, I was just expecting the wrong thing.

---

