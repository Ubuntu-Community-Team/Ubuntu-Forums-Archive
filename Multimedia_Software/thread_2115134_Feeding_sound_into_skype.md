---
title: "Feeding sound into skype"
date: 2013-02-12
forum: Multimedia Software
---

### Post by Kodiac on 2013-02-12
Hi,

I would like to do online classes about ubuntu stuff and one of the software i want them to learn is like audacity. since that software is sound intensive i was wondering if there was a way to feed all computer sounds through the microphone "IN" so that it goes through skype. Retaining my voice input is less important than the rest of the sounds, but it would be fun to keep talking while i do this too. thanks.

Oh and i tried searching the forums.. but all i get is 1000 "Microphone doesnt work" posts..

---

### Post by Thee on 2013-02-12
Ok what you are looking for is an option called called "Stereomix", "Monitor" or as its called sometimes in Windows "What You Hear".

First what you will need is to install pavucontrol, if you dont have it already:

```
sudo apt-get install pavucontrol
```

Launch pavucontrol and Audacity. In Audacity click record, now in pavucontrol select Recording tab and you will see there Audacity recording.
On the right side there is a drop down menu from which you can choose soundcard options. Click on that and select "Monitor of NEME_OF_YOUR_SOUNDCARD" that Audacity is currently using to play. This should make the mic record what ever you are playing in Audacity.

Launch Skype to test if its working.

---

