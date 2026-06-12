---
title: "Can't read from /dev/dsp"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by nighttime on 2006-08-01
Hey, well, my problem is I can't "cat" things from the sound device (/dev/dsp), I mean, I CAN output /dev/dsp's contents on the screen (while I'm playing a sound file), but all I get is an endless list of blank square characters.

What I want to be able to do is...

```

cat /dev/dsp > somefile
cat somefile > /dev/dsp
```

... and hear whatever was coming out of my speakers at the time I was writing to somefile. I've tried that and all I get is silence when I write to the sound device (I suppose it's because of fact that the output of 'cat /dev/dsp' doesn't ever change, not even when I'm playing something).

Anyway, I hope you can help me. Thanks in advance.

P.S. Btw, I've looked in other sites and

```

cat /dev/dsp > somefile
cat somefile > /dev/dsp
```

is supposed to work fine in other distros. I haven't tried it though.

---

### Post by mpvano on 2006-08-02
This only works if the sound file and the sound card agree about the exact details of the format, since there is no opportunity for either to adapt to the other.

The one common exception that proves the rule may be the test file supplied with oss drivers, but it's in a format you are not likely to want to use.

Despite the old FAQ's that tell you to do this it almost never works.

You can achieve what you are trying to do by using a program like sox (for oss) or aplay/arecord inline in your pipe to adapt the file format and configure the sound card.

You WILL, however have to use the command line options needed to tell sox or aplay/arecord all about your sound card and the file in question.

This is easier than it sounds. Just standardize on one kind of files, with a standard rate, encoding, number of channels, etc and make a bash script or command alias to handle making it transparent.

Note that you can use these commands either to replace cat, or piped via standard IO after or before the cat command.

They're very handy and reliable (if a bit confusing to figure out - both of these programs feature "the command line from hell" option interfaces).

You'll need to apt-get sox, but the others should be already installed. Note that if you want mp3 support in sox, you'll have to build it from sources yourself and make sure you have lame available.

Piping audio has its limitations (speed and buffering constraints in the pipeline), but it's an incredibly powerful tool. I've prototyped working automated file archiving systems that run 24/7 and keep 24 hour live spools of audio available for random listening using nothing but these tools, awk, and the standard unix utilities...

Sox also does almost all standard DSP operations you would want to do, so it's an amazing tool for building diagnostic utilities using nothing more than scripts...

hope this gets you started on a fascinating part of Unix....

Mario

---

