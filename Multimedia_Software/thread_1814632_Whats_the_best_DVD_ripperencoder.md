---
title: "Whats the best DVD ripper/encoder?"
date: 2011-07-29
forum: Multimedia Software
---

### Post by oxf on 2011-07-29
OK simple question..

What your recomendation for a DVD ripper to make a simple  backup, i.e DVD 9 to DVD 5 single layer? Nothing particualry fancy just needs to do the job well.  

I've never done this in Linux before

Thanks

---

### Post by zobcat on 2011-07-29
Handbrake

---

### Post by jerrrys on 2011-07-29
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=best+DVD+ripper&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=best+DVD+ripper&sa=Search&cof=FORID:9#926)

---

### Post by coffeecat on 2011-07-30
> **oxf said:**
> 
What your recomendation for a DVD ripper to make a simple  backup, i.e DVD 9 to DVD 5 single layer? Nothing particualry fancy just needs to do the job well.

If you mean to take a dual layer DVD and rip/shrink it so that it can fit on a single-layer DVD, have a look at k9copy - it's in the repos. You can copy directly to a DVD-R(W) if you have two optical drives, or rip to an ISO for burning later. You need libdvdcss2 installed if you need to copy commercial encrypted DVDs. If you don't, and try to rip an encrypted DVD, k9copy will simply fail with an unhelpful error message.

---

### Post by oxf on 2011-07-30
> **coffeecat said:**
> If you mean to take a dual layer DVD and rip/shrink it so that it can fit on a single-layer DVD, have a look at k9copy - it's in the repos. You can copy directly to a DVD-R(W) if you have two optical drives, or rip to an ISO for burning later. You need libdvdcss2 installed if you need to copy commercial encrypted DVDs. If you don't, and try to rip an encrypted DVD, k9copy will simply fail with an unhelpful error message.


OK I answering my own question now after locating the doccumentation. Appears it works under both KDE and GNOME. 

The thing that confuses me a bit still is the region code of back up DVD's. How do I ensure that my burnt DVD is reion free? i.e region 0

Thanks

---

### Post by coffeecat on 2011-07-30
When you rip the DVD, the region coding is removed. Any DVD you burn from the ISO should be region free.

---

### Post by oxf on 2011-07-30
OK understand, Thanks.
Also am I understanding this correctly? I dont need something like DVD Free in Windows to remove encryption because lbdvdcss2 takes care of it ?

---

### Post by coffeecat on 2011-07-31
That's right. The libdvdcss2 library takes care of the content scramble system. However, some of the media labels are using additional methods in an attempt to frustrate ripping, and you may come across some DVDs that k9copy/libdvdcss2 can't deal with. For example:

[http://en.wikipedia.org/wiki/ARccOS_Protection](http://en.wikipedia.org/wiki/ARccOS_Protection)

---

### Post by oxf on 2011-07-31
> **coffeecat said:**
> That's right. The libdvdcss2 library takes care of the content scramble system. However, some of the media labels are using additional methods in an attempt to frustrate ripping, and you may come across some DVDs that k9copy/libdvdcss2 can't deal with. For example:

[http://en.wikipedia.org/wiki/ARccOS_Protection](http://en.wikipedia.org/wiki/ARccOS_Protection)

OK thanks for that too. :)
Katja

---

### Post by Viaoiwohi on 2011-08-27
Yes&#65292;Handbrake.

---

### Post by shantiq on 2011-08-27
[**handbrake **]("https://edge.launchpad.net/~stebbins/+archive/handbrake-releases")is awesome and so is OGMrip as GUI


you will need to edit your software sources to Lucid for the handbrake ppa


OGMrip is in your synaptic


==============================

**[SIZE="2"][FONT="Comic Sans MS"]or even much easier[/FONT][/SIZE]**  one line command line

```
sudo apt-get install dvdbackup
```


then only one simple line


```
dvdbackup -M
``` for entire dvd

```
dvdbackup -F
``` for main feature of  dvd


    how simple is this?

---

### Post by marinegundoctor on 2011-08-29
While Handbrake is a great tool (I use it regularly) it is not what the OP needed for the task presented. OGMrip wouldn't do this wither. He wants to backup a DVD to a single layer, so DVD95, K9copy, and dvdbackup are all good programs that will backup a DVD9 to a DVD5;

---

