---
title: "Looking for &quot;audio DSP experimenter's workbench&quot; type application: what is it called?"
date: 2022-01-20
forum: Multimedia Software
---

### Post by wb0gaz on 2022-01-20
I'm in need of a way to develop (in C language) audio stream processing applications on PC desktop rather than in embedded system (which would eventually target the resulting code.) This is for learning/experimentation, not production use.

My need is for something like this:

1. Audio input (two channels left and right) from outside world delivered to PC sound peripheral left and right inputs.
2. Audio samples accepted from sound peripheral inputs to Ubuntu linux sound subsystem
3. Audio input samples in the Ubuntu linux sound subsystem become a stream of data (bytes/words/etc.) available to a C-language program written (by user/experimenter) for Ubuntu PC
4. C-language program does it's work (whatever the learner's operation might be)
5. Audio output samples are a stream of data emitted from C-language program
6. Stream of output audio samples delivered by C-language program back to Ubuntu linux sound subsystem
7. Processed audio (two channels left and right) emerge from sound card

The C-language program isn't defined - that's what would be developed. The simplest version might be to simply copy each received audio sample to become a processed output audio sample (so that what arrives on the stereo input of the PC sound peripheral emerges on the stereo output of the same PC sound peripheral.) Beyond that, no "canned" or other stuff is needed, just a way to process audio samples in a C-language program that would be written for experimentation and learning.

Does this sort of thing exist (if so, what is it called and where should I look?)

I'd hate to re-invent the wheel as this seems like a very likely application to already exist.

Thank you for any advice, and of course any questions or requests for clarification will be answered!

Dave

---

