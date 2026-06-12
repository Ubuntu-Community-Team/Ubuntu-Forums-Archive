---
title: "I can't get sound from line-in using tvtime eventhough sound received from TV card."
date: 2012-05-30
forum: Multimedia Software
---

### Post by Blackie_Chan on 2012-05-30
I just installed Ubuntu 12.04 32-bit and usually run tvtime on my computer. 

When I run tvtime, I get hear no sound. With tvtime running, when I click on 'Sound Settings', select the Input tab. I see Record sound from Line In, and the Input level moves to indicating that sounds is received from my tvcard.

I checked alsamixer and non on the controls are on mute. 

I am able to watch flash videos online, play .avi videos and listen to mp3s and I get audio. It's just with tvtime that I get sound problems.

What changes can I make to fix the audio problem with tvtime?

I have found a workaround. I run `gstreamer-properties` from terminal. In the Audio tab, under Default Input, I have to click on the Test button. When the Testing Pipeline dialog box shows up, I'll be able to hear sound from tvtime. When I close the Testing Pipeline window, I get no sound from tvtime.

See screenshots below with some of the windows I'm describing.

---

### Post by Blackie_Chan on 2012-05-31
> **Blackie_Chan said:**
> I just installed Ubuntu 12.04 32-bit and usually run tvtime on my computer. 

When I run tvtime, I get hear no sound. With tvtime running, when I click on 'Sound Settings', select the Input tab. I see Record sound from Line In, and the Input level moves to indicating that sounds is received from my tvcard.

I checked alsamixer and non on the controls are on mute. 

I am able to watch flash videos online, play .avi videos and listen to mp3s and I get audio. It's just with tvtime that I get sound problems.

What changes can I make to fix the audio problem with tvtime?

I have found a workaround. I run `gstreamer-properties` from terminal. In the Audio tab, under Default Input, I have to click on the Test button. When the Testing Pipeline dialog box shows up, I'll be able to hear sound from tvtime. When I close the Testing Pipeline window, I get no sound from tvtime.

See screenshots below with some of the windows I'm describing.

Adding screenshots
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218988&d=1338435518[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218989&d=1338435518[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218987&d=1338435518[/IMG]

---

