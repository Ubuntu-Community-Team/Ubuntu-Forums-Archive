---
title: "Feisty - problem with gstreamer-properties and surround sound"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by David Eikelenboom on 2007-04-26
Hi there!

After upgrading to Ubuntu 7.04 I can't get my surround sound working.
When running gstreamer-properties, and pressing the test-button for testing the default sound output, the sound is jerky.
Changing the settings for the plugin from ALSA to manually adjusted (I don't know if that is the correct english term, I am using a dutch interface) and setting the pipeline to
alsasink device=ch51dup, the sound, using the test button is OK again.
The problem is that after closing gstreamer-properties, those new settings are lost. When running gstreamer-properties again the settings are reverted back to the standard settings.

How do I get my system to remember the correct settings, so it uses my own adjustments in /etc/asound.conf again?

Regards,
David,

---

