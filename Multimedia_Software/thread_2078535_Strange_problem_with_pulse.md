---
title: "Strange problem with pulse"
date: 2012-10-31
forum: Multimedia Software
---

### Post by perjarle on 2012-10-31
Hello all
I'm having a strange problem that I think is related to pulseaudio, even though it doesn't seem logical.

I'm writing a Java application for decoding and displaying video streams from an ip camera.
I use Xuggler for decoding.

After having trouble with the audio, I followed this guide to make Java Sound Engine available:
[http://www.realitysend.com/kirbj/devlog/linuxsound](http://www.realitysend.com/kirbj/devlog/linuxsound)

Then I got the sound working.

But my Java application needs to run some Linux commands such as "ping", "amixer" and "wget" from time to time.
The Java code I'm using for calling those commands is as follows:
```

Process p = Runtime.getRuntime().exec(command);
exitCode = p.waitFor();

```Every time this code is ran, I get the following error:
 *[COLOR=black][FONT=&quot]Assertion 'pa_atomic_load(&(b)->_ref) > 0' failed at pulsecore/memblock.c:589, function pa_memblock_unref(). Aborting.[/FONT][/COLOR]*


[COLOR=black][FONT=&quot]Then the application dies.
[/FONT][/COLOR]
  
Before upgrading from Ubuntu 10.04 to 12.04 I had OSS (Open Sound System) installed, and it worked perfectly.
But OSS is deprecated.

Does someone know what may be the problem?
Are there any libraries that needs an update?

Best regards
Per-Jarle

---

