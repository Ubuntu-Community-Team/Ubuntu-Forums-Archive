---
title: "using ffmpeg but getting &quot;unsupported codec&quot; error"
date: 2008-08-12
forum: Multimedia Software
---

### Post by chris_tikva on 2008-08-12
I've just downloaded ffmpeg for the main purpose of extracting the audio from a mpg file. I've tried various combinations of the command line in the examples but always get "unsupported codec (id=86020) for input stream". 

I've tried to find information on this but can't find what I want so I'm stymied. Any tips?

Thanks

Chris

---

### Post by zuner2012 on 2008-08-12
which audio program are you using, some have built in codec searching

---

### Post by chris_tikva on 2008-08-12
I'm just using ffmpeg and an mpg file which was captured from a DVD I recorded from the TV. Do I need something extra to make ffmpeg function?

---

### Post by kostkon on 2008-08-12
> **chris_tikva said:**
> I've just downloaded ffmpeg for the main purpose of extracting the audio from a mpg file. I've tried various combinations of the command line in the examples but always get "unsupported codec (id=86020) for input stream". 

I've tried to find information on this but can't find what I want so I'm stymied. Any tips?

Thanks

Chris
You should better get the version of *FFmpeg* provided by the [*Medibuntu* repository]("http://medibuntu.org/") that has the support for restricted formats enabled.

Thus, add this repository to your software sources list (instructions are on *Medibuntu*'s site) and then install *FFmpeg* from *Synaptic*.

---

