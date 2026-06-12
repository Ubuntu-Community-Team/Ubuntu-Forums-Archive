---
title: "pdftk *.pdf cat &lt;outfile.pdf&gt; throws java errors (if wildcards regex used)"
date: 2014-09-01
forum: Multimedia Software
---

### Post by ski_phreak on 2014-09-01
I have a (k)ubuntu specific error when I run pdftk with wildcards trying to combine (cat) multiple PDFs.

I tested this with a laptop running SolydK (a fork of Mint) and no errors.
I tested this using copies of the files (rather than links) and got the same error.

```

>pdftk *.pdf cat output combined.pdf
Error: Unexpected Exception in open_reader()
Unhandled Java Exception:
java.lang.NullPointerException
   at gnu.gcj.runtime.NameFinder.lookup(libgcj.so.14)
   at java.lang.Throwable.getStackTrace(libgcj.so.14)
   at java.lang.Throwable.stackTraceString(libgcj.so.14)
   at java.lang.Throwable.printStackTrace(libgcj.so.14)
   at java.lang.Throwable.printStackTrace(libgcj.so.14)

```

Combining the same files by typing each one individually bypasses the error (but there's no way I can afford to do so with all the sheetmusic I need to collate.)
```

>pdftk 01_Handel_Aria_celloBass.pdf 11_Bach_JesuJoyOfMansDesiring_celloBass_p01.pdf 11_Bach_JesuJoyOfMansDesiring_celloBass_p02.pdf Porter_cello_p2-02_NightAndDay.pdf Porter_cello_p2-03_NightAndDay.pdf cat output combined.pdf

```

I already tried recompiling pdftk from source in case my libraries and paths were different than it expected.  I stopped short of recompiloing gcj since that wanted to recompile all of gcc.
```

>sudo apt-get -b source pdftk
>sudo dpkg -i pdftk_2.01-1_amd64.deb 

```

I couldn't find anything like it out there in web-land.  Any ideas?
Any command-line replacement that I could use instead of pdftk?  

If it helps any, PDFChain fails with the same error.  PDFShuffler works fine, but I really need a scriptable solution, not either gui.

Here's the system specs that may be relevant:
Kubuntu 14.04 LTS

```

>uname -a
Linux ymir-Dimension-E521 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

>dpkg -l kde* = 4:4.13.3 on all the libs and apps.
>dpkg -l pdftk
ii  pdftk                     2.01-1            amd64             tool for manipulating PDF documents

>dpkg -l gcj*
ii  gcj-4.8                   4.8.2-19ubuntu1   amd64
ii  gcj-4.8-jdk               4.8.2-19ubuntu1   amd64
ii  gcj-4.8-jre               4.8.2-19ubuntu1   amd64
ii  gcj-4.8-jre-headless      4.8.2-19ubuntu1   amd64
ii  gcj-4.8-jre-lib           4.8.2-19ubuntu1   all
(and some earlier uninstalled versions)

```

Thanks in advance.  (Linux users are awesome at helping out.  (Beats anything that some Pakistani-outsources Windows call center can ever do...i.e. just blame at the OS, other installed SW, the phase of the moon, PEBCAK, id10T, or anything that might end the call quickest.)

---

### Post by steeldriver on 2014-09-06
That's odd - glob expansion by the shell should happen before the command is run, so as far as pdftk is concerned there should be no difference whether you use *.pdf or list the files by hand - EXCEPT from the nullglob case. Are those EXACTLY the files that you get e.g. when you 'echo *.pdf' in the directory where you're running this from? Or are there many more (possibly too many for the max arg length?)

---

### Post by ski_phreak on 2014-09-09
I see what you're thinking.  Some of my filenames run long, and there can be a lot of them.

Sadly, it doesn't seem to matter.  A subset of files (PDF originals, before I convert all the scanned JPGs into PDFs) gives the same error with the 5 files:

```

>echo *.pdf
AngryBirds_bass.pdf AnneOfGreenGables_celloBass.pdf AtLast_celloBass.pdf bach-air-celloBass.pdf UnchainedMelody_bass.pdf

```

```

>pdftk *.pdf cat output combined.pdf

Error: Unexpected Exception in open_reader()
Unhandled Java Exception:
java.lang.NullPointerException
   at gnu.gcj.runtime.NameFinder.lookup(libgcj.so.14)
   at java.lang.Throwable.getStackTrace(libgcj.so.14)
   at java.lang.Throwable.stackTraceString(libgcj.so.14)
   at java.lang.Throwable.printStackTrace(libgcj.so.14)
   at java.lang.Throwable.printStackTrace(libgcj.so.14)

```

---

### Post by PopsTheSailor on 2015-01-06
So is there any fix to this? I'm not sure I'm following everything. I  have a shop manual for my car. It is broken up into about 120 PDFs that I  want to combine because I can never find the right manual to start my  search when working on my car. I get the exact same error.

What do I need to do?

---

### Post by Holger_Gehrke on 2015-01-09
You might give 'pdfunite' from the poppler-utils package a try.

---

### Post by steeldriver on 2015-01-09
I was able to try pdftk with a * glob on 12.04 and it worked fine - only breaking (gracefully) if the specified output file already existed (i.e. it tries to cat the output.pdf to itself)

```

~/pdftk_test$ ls
test-10.pdf  test-12.pdf  test-14.pdf  test-16.pdf  test-18.pdf  test-1.pdf   test-21.pdf  test-23.pdf  test-2.pdf  test-4.pdf  test-6.pdf  test-8.pdf
test-11.pdf  test-13.pdf  test-15.pdf  test-17.pdf  test-19.pdf  test-20.pdf  test-22.pdf  test-24.pdf  test-3.pdf  test-5.pdf  test-7.pdf  test-9.pdf
~/pdftk_test$
~/pdftk_test$ pdftk *.pdf cat output combined.pdf
~/pdftk_test$
~/pdftk_test$ pdftk *.pdf cat output combined.pdf
Error: The given output filename: combined.pdf
   matches an input filename.  Exiting.
Errors encountered.  No output created.
Done.  Input errors, so no output created.

```

Maybe later versions don't handle that so gracefully - can you confirm that you **don't** have a combined.pdf file in the directory?

---

