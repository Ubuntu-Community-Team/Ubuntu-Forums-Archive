---
title: "Converting bin and cue files to iso with Binchunker"
date: 2009-07-23
forum: Multimedia Software
---

### Post by tswann on 2009-07-23
Hi

I'm trying to follow your instructions for Binchunker to convert bin and cue files to iso format.  I've followed all the instructions so far but when it comes to trying to convert the files it doesn't work.  To make it simple, what I'm trying to convert is the downloaded bin and cue files for the game Star Trek Armada 2.  The files are in the folder home/thomas/StartrekAramda2 and are named Aramda2.bin and Armada2.cue.  What I'm writing in the terminal is the following:

sudo bchunk -v home/thomas/StartrekAramda2/Aramda2.bin home/thomas/StartrekAramda2/Armada2.cue Armada

When I execute this command it says:

Could not open BIN ....bin: No such file or directory

I've also tried it without the file location (just Armada2.bin Armada2.cue) and I get the same result.

Does anyone know how I can solve this problem?

Yours,

Thomas

---

### Post by jerome1232 on 2009-07-23
Try

```
sudo bchunk -v /home/thomas/StartrekAramda2/Aramda2.bin /home/thomas/StartrekAramda2/Armada2.cue Armada
```

---

### Post by tswann on 2009-07-23
Thanks for the fast response, but I'm afraid I got the same message as previously.

---

### Post by jerome1232 on 2009-07-23
try writing the first part of the command then hit space and drag the .bin file into your terminal, hit space again then drag the .cue file into your terminal.

---

### Post by tswann on 2009-07-23
That worked!  Thank you.  In the terminal it inserted ' before and after each file name.

---

### Post by dwlamb on 2012-06-17
I am trying to use bchunker with this syntax

```
bchunk /pathto/cd15.bin /pathto/cd15.cue  /pathto/cd15.iso
```and it makes a mess by only extracting the files to the path, not writing them into an ISO. 

What am I doing wrong?

---

