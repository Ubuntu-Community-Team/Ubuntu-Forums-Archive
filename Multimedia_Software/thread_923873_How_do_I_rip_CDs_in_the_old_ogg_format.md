---
title: "How do I rip CDs in the old ogg format?"
date: 2008-09-18
forum: Multimedia Software
---

### Post by jmate24 on 2008-09-18
Hi, I am wondering how to rip my CDs into the old .ogg format?
And I am currently using Ubuntu Intrepid Ibex 8.10 and Audio CD Extractor (old Sound Juicer).

---

### Post by rfdparker2002 on 2008-10-15
Its technically the same format (Ogg Vorbis), but since Ogg is really just a container format for vorbis (audio) and theora (video), it would seem they are trying to be more specific with .oga and .ogv, but personally I believe making this change to the Sound Juicer defaults was a mistakes, as many apps only look for .ogg and no .oga when looking for audio (e.g. ampache).

But luckily there is a easy solution to this:
[LIST=1]
[*]From the 'Edit' menu choose 'Preferences'
[*]Assure the output is set to 'CD Quality, Lossy (.oga type)'
[*]Click the 'Edit Profiles...' button
[*]In the resulting window select 'CD Quality, Lossy'
[*]Click the 'Edit' button
[*]In the 'File extension' text box replace 'oga' with 'ogg'
[*]Click the 'Close' button on the current and two other windows
[/LIST]

---

### Post by ubundude on 2008-10-25
This just begs the question - why the hell change it in the first place. I went though all this trouble to make my ipod play *.ogg files so I could could be open source, and on this new release you change something so small...but now I have to go trolling around in yet another bunch of forum post to solve a problem that should not be.  This is just the kind of thing that is holding back the LINUX community as a whole. Every release until now has ripped to *.ogg by default...why I ask, why change it now? The easy thing for me to do would be to re-boot in to windows and rip to mp3 then sync, I would be done by now, as it is you changed what I expected to happen and cost me a head ache, I hope some one see this and changes it in the final release, only 5 days left.

---

### Post by steveydoteu on 2008-10-25
> **ubundude said:**
> This just begs the question - why the hell change it in the first place.

[http://www.stevey.eu/2008/10/sound-juicer-missing-in-intrepid/](http://www.stevey.eu/2008/10/sound-juicer-missing-in-intrepid/)

---

### Post by ubundude on 2008-10-25
Your just shifting blame. People are going to expect a smooth transition to ibex, changing little things like this makes people frustrated. Who ever is to blame should have thought it out better. Im not complaining about it not being installed by default, (by the way is any ripper installed by default?). I hacked my ipod to play *.ogg files not *.oga files, I cannot even find a hack to make any stand alone player decompress *.oga. What I'm saying is the community went thought all this trouble to establish a standard i.e *.ogg, why change it!?! why? Your shooting your self in the foot!

(edit) Guess I should have read the page before firing off a response, so the codec have changed and my ipod my not be able to play it anyway....thats just great....I'm speachless.

---

### Post by steveydoteu on 2008-10-25
> **ubundude said:**
> Your just shifting blame. People are going to expect a smooth transition to ibex, changing little things like this makes people frustrated. Who ever is to blame should have thought it out better. Im not complaining about it not being installed by default, (by the way is any ripper installed by default?). I hacked my ipod to play *.ogg files not *.oga files, I cannot even find a hack to make any stand alone player decompress *.oga. What I'm saying is the community went thought all this trouble to establish a standard i.e *.ogg, why change it!?! why? Your shooting your self in the foot!

(edit) Guess I should have read the page before firing off a response, so the codec have changed and my ipod my not be able to play it anyway....thats just great....I'm speachless.

You have misinterpreted it, the encoder is the same the **extension **is different but can easily be altered. It is a change to use the standard formats, rather than a container.

As mentioned [previously]("http://ubuntuforums.org/showpost.php?p=5972552&postcount=2") in the topic: **.oga **is ogg audio (Vorbis) and **.ogv **video (Theora), it actually makes a lot of sense to use the oga format, just happens presently not everything handles it as expected.

Ubuntu are not the developers for sound-juicer and the GNOME audio profiles are not a direct part of it either, although it, like most audio extractors would implement it.

You can read here in the GNOME documents regarding sound-juicer albeit for the previous version, that it is documented how to alter the profiles:

[http://library.gnome.org/users/sound-juicer/stable/preferences.html.en_GB#prefs-format](http://library.gnome.org/users/sound-juicer/stable/preferences.html.en_GB#prefs-format)

Adding to this, the links given in my [blog entry]("http://www.stevey.eu/2008/10/sound-juicer-missing-in-intrepid/") also give information on [changing the profile]("http://stevepearce.info/blog/2008/10/17/sound-juicer-changes-in-intrepid-ibex/") from OGA to an OGG extension.

Rather than jumping to assumptions take more time to read and research, and above all ask questions. Panic over.

---

