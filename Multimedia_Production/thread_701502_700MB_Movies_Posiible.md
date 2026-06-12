---
title: "700MB Movies?? Posiible?"
date: 2008-02-19
forum: Multimedia Production
---

### Post by Cariro on 2008-02-19
The title says it all, but i want to know if there is a program that can make 700mb movie files, and if so, can someone post a tutorial?

I've got k9copy, but don't know if this can make 700mb files or how to use the program at all.

Thanks for the help.

---

### Post by stealthbanana on 2008-02-19
Look at the dvdrip application.  It very good documentation and you can farm out the transcoding across your network.

---

### Post by Cariro on 2008-02-19
Thanks man!

---

### Post by koleoptero on 2008-02-19
Or for an even easier solution, try thoggen.

---

### Post by gsmanners on 2008-02-20
I assume from the response that this is about DVD ripping?

If you want to preserve the relative quality and resolution, and if we're talking about movies (around 90 or so minutes long), you're going to need to use something like x264 for your encoding to get under 700 MB.

---

### Post by dcast on 2008-02-20
I like AcidRip for this, seems to work faster than most and not quite as complex as dvd::rip.

---

### Post by michaelzap on 2008-02-20
> **gsmanners said:**
> I assume from the response that this is about DVD ripping?

If you want to preserve the relative quality and resolution, and if we're talking about movies (around 90 or so minutes long), you're going to need to use something like x264 for your encoding to get under 700 MB.

Or two-pass xvid with a variable bit rate. I usually do that and copy the existing ac3 stereo audio from DVD movies, and that gets most of them down between 700 and 800 MB easily. I've gotten the best quality from Avidemux (open the first VOB file, join them, set your options and save the file), but AcidRip also does a pretty good job (although for some reason xvid in particular looks worse from AcidRip).

---

### Post by gsmanners on 2008-02-20
You can get decent quality from Xvid, but if the movie goes over 2 hours you'll almost certainly need to split it over two discs.

---

### Post by ThndrChckn on 2008-02-21
if you use mencoder single pass do this...

Single pass

mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=687 -o <output.avi> <input.avi> 

if its in a dvd drive put dvd:// before -ovc and get ride of <input.avi>

two pass is...

mencoder dvd:// -oac mp3lame -ovc xvid -xvidencopts pass=1 -o /dev/null
mencoder dvd:// -oac mp3lame -ovc xvid -xvidencopts pass=2:bitrate=800 -o <filename.avi>

use this link to find more about [mencoder]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#XviD_One-Pass_Encoding")

---

### Post by eye208 on 2008-02-21
Don't use Xvid unless you need it for compatibility. x264 will yield superior quality at comparable file sizes. Look at these examples:

Xvid:
[img]http://img295.imageshack.us/img295/8960/xvid0297gj1.png[/img]

x264:
[img]http://img524.imageshack.us/img524/222/x2640297ii3.png[/img]

Xvid:
[img]http://img183.imageshack.us/img183/8549/xvid7478od4.png[/img]

x264:
[img]http://img526.imageshack.us/img526/206/x2647478rd1.png[/img]

---

### Post by gsmanners on 2008-02-21
With 704x396, you can probably get away with about 500 to 600 kbps with x264, but you'll need to go at least 800 to 900 with Xvid to get about the same quality.

---

### Post by michaelzap on 2008-02-21
> **gsmanners said:**
> With 704x396, you can probably get away with about 500 to 600 kbps with x264, but you'll need to go at least 800 to 900 with Xvid to get about the same quality.

x264 definitely yields better quality at lower bit rates. But a lot of players still don't support it (my DVD player doesn't), and it takes a whole lot more CPU and time to make (and a lot more CPU to play them as well). So that's why I still use xvid for now, but that's just me.

---

### Post by ThndrChckn on 2008-02-21
when i posted about ripping with mencoder i didn't mean you had to use xvid. The codecs that you can use are listed on the wiki. x264 can be used. I just used xvid as an example as i use it for my movies. Its personal preference.

---

