---
title: "Sharing the Print to PDF Printer to a Windows machine"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by ABitTooSpicy on 2009-02-02
Hi Everyone,

I have been struggling with a problem for a couple of days now and after trying lots of different things and banging my head against my keyboard I have decided the only way to fix my issue is to get help!  So please help!! (And I apologize if this is a newbie question).

I am attempting to make my ubuntu box a document server.  Print to PDF works perfect on the machine (Which is ubuntu 8.10).  I also want all the other computers on the network to be able to access the pdf printer.  So I followed the guide here - [http://ubuntuforums.org/showthread.php?t=806699&highlight=printer+sharing](http://ubuntuforums.org/showthread.php?t=806699&highlight=printer+sharing)

The issue comes on the windows xp side when I try to add the printer.  No matter what drivers I select, the spoolsv service hangs before completion of the add.  If I kill the spoolsv process and restart it, the printer is indeed listed and I am able to send one print job to ubuntu, (which looks like it completes, but I can't find the document in the [home]/pdf location or the ANONYMOUS location)  After that 1st doc is sent, spoolsv again spikes to 100% cpu util and I am no longer able to print any other documents.  

I have no idea what to do differently!  Help a newbie please!

---

