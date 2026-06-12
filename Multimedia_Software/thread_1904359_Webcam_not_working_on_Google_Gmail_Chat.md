---
title: "Webcam not working on Google/ Gmail Chat"
date: 2012-01-04
forum: Multimedia Software
---

### Post by tango_ninja on 2012-01-04
Please let me know if this is not the correct forum for this question.

The voice/video chat browser plugin in Gmail is not working.  When I try to make a video call, it crashes.  In Google Chrome, this is manifested by the error message: "The following plug-in has crashed: /opt/google/talkplugin/libnpgtpo3dautoplugin.so"  In Firefox (8.0) this is manifested by the error "Google Talk Video Accelerator plugin has crashed."  I am running Ubuntu 11.04 (x86).

Gmail detects my webcam (Logitech C525) and it appears under the drop-down menu in Settings > Chat > Camera.  My name also has a little video camera in the chat window.  When I try to chat, audio works but the screen remains blank.  I cannot see anyone, and they cannot see me.  However, when I try to chat without my webcam, I can see others if they provide their video feed.  

[B]What I've already tried:
[/B]- Trying everything in both Google Chrome and Firefox
- Testing webcam video/audio in Cheese and Skype.  Everything works fine in both.
- Upgrading to the new v 2.5.6.0 Google Talk Plugin (prev v 2.2)
- Turning the 'Video Chat Enhancements' lab on and off
- Turning the 'Advanced Attachment Features' on and off (who knows, someone suggested it)
- Disabling/enabling plugin /opt/google/talkplugin/libnpgoogletalk.so
- Disabling/enabling plugin /opt/google/talkplugin/libnpgtpo3dautoplugin.so
- Defining **LIBGL_ALWAYS_SOFTWARE=1** in */opt/google/talkplugin/envvars* (This is supposed to bypass OpenGL and hardware acceleration as per [http://www.linuxquestions.org/questions/slackware-14/google-talk-plugin-slackware64-current-google-chrome-latest-and-multilib-error-853546/](http://www.linuxquestions.org/questions/slackware-14/google-talk-plugin-slackware64-current-google-chrome-latest-and-multilib-error-853546/))

Any ideas?

---

### Post by tango_ninja on 2012-01-13
Any takers?

---

### Post by KDMerrill on 2012-02-07
Having the exact same issue.....did you ever get it resolved?

---

### Post by tango_ninja on 2012-02-08
> **KDMerrill said:**
> Having the exact same issue.....did you ever get it resolved?

Never got it resolved but determined that it is due to my crappy laptop hardware.  It doesn't support hardware acceleration in ubuntu and it seems google talk needs this enabled.

---

### Post by Francewhoa on 2012-03-26
Same here. In my case it does not work with Firefox 10.0.2 but it works with Chrome 12.0.742.112.

You can test your webcam at [http://www.testwebcam.com](http://www.testwebcam.com)

---

### Post by rojepower on 2012-10-14
Hi,

I have some troubles using my webcam. It is working with gstreamer-properties, it's working with a google hangout on firefox and chrome but it's not working on other sites like testwebcam.com or with the webrtc demo on [http://labs.opentok.com/try/](http://labs.opentok.com/try/)

How can I make chrome or firefox access to my webcam properly ?

Thanks for your advices.

---

