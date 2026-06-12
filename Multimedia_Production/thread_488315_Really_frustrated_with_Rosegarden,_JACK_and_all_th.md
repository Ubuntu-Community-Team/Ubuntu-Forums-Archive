---
title: "Really frustrated with Rosegarden, JACK and all this nonsense - Help me setup midi..."
date: 2007-06-30
forum: Multimedia Production
---

### Post by CPtAJ on 2007-06-30
I'm really having some trouble setting this thing up. I iinstalled the ubuntu studio audio package figuring hey, this should be enough... wrong. From the start, tell me how to set this thing up.

I have an Audigy MP3+ and a lowlatency kernel already installed. Whats next?

---

### Post by stijngysemans on 2007-06-30
what is the exact problem you encountering?

---

### Post by CPtAJ on 2007-06-30
Oh I'm sorry, the problem is that there's no midi. No sound coming from midi. I try to get some sound out of rosegarden and fail miserably.

Figured that was understood from my post. My bad.

---

### Post by robertc36 on 2007-07-02
Having similar problems .Am running Ubuntu studio .
I have a Yamaha Psr keyboard and was initially impressed when the system recognised it.
None of the recording apps do though and cannot understand why the signal is not recognised.
As a musician really wanted to get recording.
I have got my microphone working though so am back to recording acoustically.
Still to early for me to fully understand linux architecture to chase down the problem.
I am not going back to windows but i miss rewire lol.

---

### Post by EmaRsk on 2007-07-03
Hi. I had problems too figuring out.

Here is how I get rosegarden working:
[LIST]
[*]start qjackctl
[*]start qsynth
[*]start rosegarden
[/LIST]

There are a couple of things to check:
[LIST]
[*]connections (with qjackctl): rosegarden general midi -> fluidsynth input (qsynth is a GUI frontend to fluidsynth)
[*]qsynth must be configured to use jack (of course) and to load some soundfont (.sf2 file).
[/LIST]

You can download some soundfonts [here]("http://pages.sbcglobal.net/joethedude/downloads_section/soundfonts_mainpage.html").

Hope to have been helpful.

---

### Post by robertc36 on 2007-07-03
Not my thread but thanks for the post.
Will give it all another try

---

### Post by CPtAJ on 2007-07-03
Hey, thanks for the reply. I had completely given up on this thread. I went to the IRC channel and was pointed to this guide:
[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

It eventually worked with that. I'm sure jack is still boned and recording doesn't work but I don't have a keyboard right now so its fine for now. Rosegarden works perfectly now though so I'm happy ;)

---

### Post by sp200606 on 2008-06-02
Thanks for those few lines. I was just forgetting to launch qSynth...

---

