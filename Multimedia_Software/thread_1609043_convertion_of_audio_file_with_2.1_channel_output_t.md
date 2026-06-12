---
title: "convertion of audio file with 2.1 channel output to 5.1"
date: 2010-10-29
forum: Multimedia Software
---

### Post by ashu. on 2010-10-29
[B]Sorry this could be a wrong place to ask this question but this is the only place i got correct answer to many of my questions so asking it...

Is it possible to convert a 2.1 channel mp3 or any video file to get a respective 5.1 file permanently so i could play them on external music system which is 5.1 speaker system...

if yes plz give me the software or tool name..
if not possible can u suggest me sites where i can usually songs n video with 5.1 channel...plz plz plz reply..:(
[/B]

---

### Post by Old_Man_Unix on 2010-10-30
Yes it is possible.  Although you cannot create true surround sound audio - since you only have two channels to start with - you can fake  a pseudo-surround with the proper tool.

The tool you want (command line) is called **SoX** (Sound Exchange).  You can install it from the repositories.  See the **SoX** manual for how to do channel conversions - there are different ways to go about it depending on the original source and what you are trying to achieve.

Fair warning - **SoX** is a complex application with many options and effects - channel conversions being just one of many.    There is definitely a learning curve associated with it.     

Also, as with any digital audio processing, sometimes you have to play around a bit to get exactly what you want.

Remember to keep an archive copy of the original audio file so you can get it back if you mess up.

Good luck.

---

### Post by ashu. on 2010-10-30
> **Old_Man_Unix said:**
> Yes it is possible.  Although you cannot create true surround sound audio - since you only have two channels to start with - you can fake  a pseudo-surround with the proper tool.

The tool you want (command line) is called **SoX** (Sound Exchange).  You can install it from the repositories.  See the **SoX** manual for how to do channel conversions - there are different ways to go about it depending on the original source and what you are trying to achieve.

Fair warning - **SoX** is a complex application with many options and effects - channel conversions being just one of many.    There is definitely a learning curve associated with it.     

Also, as with any digital audio processing, sometimes you have to play around a bit to get exactly what you want.

Remember to keep an archive copy of the original audio file so you can get it back if you mess up.

Good luck.
thank you very much i use it now...

---

