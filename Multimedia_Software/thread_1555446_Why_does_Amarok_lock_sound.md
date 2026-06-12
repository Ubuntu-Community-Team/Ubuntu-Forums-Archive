---
title: "Why does Amarok lock sound?"
date: 2010-08-18
forum: Multimedia Software
---

### Post by Roasted on 2010-08-18
It doesn't make sense to me why you would want sound to be disabled system wide EXCEPT for Amarok. So I come here asking this question.

I can use YouTube and Audacious at the same time, sound running on both. I cannot do this with Amarok and YouTube, which I would like to do, since it's nothing short of a pain in the *** otherwise.

How can I adjust this?

Are there any programs like this?

Do all KDE applications do this?

Does KDE have pulse audio? If not, when will they get it?

If I am running Ubuntu 10.04 w/ Kubuntu-Desktop installed, would KDE be running on pulse audio then?

---

### Post by halfbeing on 2010-08-25
I'm guessing that you have a simple sound card of the kind you would find in a laptop and that you are therefore using a sound server, probably PulseAudio, to allow applications to share the audio out.

If so, go to the "Multimedia" option in the KDE system settings panel. Check the priority of the sound devices in the "Music" option. If you have something that looks like the name of your sound card at the top, with PulseAudio somewhere below it, that will be the cause of your problem. Only one application can use the sound output at a time, so you want it to be PulseAudio and not one of your desktop applications. Drag PulseAudio to the top of the list so that Amarok will use PulseAudio rather than compete with it, and you'll be done (if I guessed correctly of course).

---

### Post by Roasted on 2010-08-25
> **halfbeing said:**
> I'm guessing that you have a simple sound card of the kind you would find in a laptop and that you are therefore using a sound server, probably PulseAudio, to allow applications to share the audio out.

If so, go to the "Multimedia" option in the KDE system settings panel. Check the priority of the sound devices in the "Music" option. If you have something that looks like the name of your sound card at the top, with PulseAudio somewhere below it, that will be the cause of your problem. Only one application can use the sound output at a time, so you want it to be PulseAudio and not one of your desktop applications. Drag PulseAudio to the top of the list so that Amarok will use PulseAudio rather than compete with it, and you'll be done (if I guessed correctly of course).

I have seen this on both laptops and desktops with upgraded dedicated sound cards. No matter what, Kubuntu exhibits these same issues. It seems a little confusing that it would do that, since it requires tweaking to get to work "right."

---

