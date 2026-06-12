---
title: "Basic Command Line Help"
date: 2013-02-05
forum: Multimedia Software
---

### Post by OsakaWilson on 2013-02-05
Hello.

I have a .gig file and need to extract the .wav files from it. 

I have installed Gig Tools, which includes Gigextract, a command line application. 

It comes with the description below. I understand that I need to type into the command line. 

I tried typing in:
 
gigextract maestro_concert_grand_v2.gig Music

That didn't work. I understand that GIGFILE means the name of the .gig file. I put that in the command. Also DESTDIR means destination directory. The name of the directory I'd like it to go to is called Music. All I get is: Invalid input file argument!

Can anyone tell me what I'm doing wrong? 

----------------------------

SYNOPSIS

       gigextract [ -v ] GIGFILE DESTDIR [SAMPLENR] [ [SAMPLENR] ... ]

DESCRIPTION

       Extract  samples  from  Gigasampler (.gig) files. All extracted samples
       will be written in .wav format. You must at least supply  name  of  the
       .gig  input  file and an output path where all extracted samples should
       be written to. By default gigextract extracts all samples contained  in
       the  Gigasampler file, even if they are not linked by any instrument in
       the .gig file, but you can also  extract  only  particular  samples  by
       supplying a list of samples indices at the end of the command line. You
       can use the gigdump tool to see the list of available samples and their
       sample indices of a Gigasampler file.

OPTIONS

        GIGFILE
              filename of the input Gigasampler file

        DESTDIR
              output path where all samples should be extracted to

        SAMPLENR
              optional index of sample(s) to be exclusively extracted

        -v    print version and exit

---

### Post by PowerBarry43 on 2013-02-05
Hi

That looks fine to me. The only thing I can think of is that you aren't using full paths.

try:

```
~/gigextract maestro_concert_grand_v2.gig ~/Music/
```The problem could of course be as simple as an incorrect filename.... remember linux is very case sensitive. Try just typing maestro or ~/maestro and hit tab to auto-complete the filename, if the auto-completion doesn't happen thats probably your problem.

Hope this helps!

Barry

---

