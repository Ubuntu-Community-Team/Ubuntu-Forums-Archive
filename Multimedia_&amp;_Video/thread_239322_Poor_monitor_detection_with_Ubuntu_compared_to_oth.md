---
title: "Poor monitor detection with Ubuntu compared to other distros ?"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by Strykaas on 2006-08-19
Hello all,

I started Linux at home about two month ago, and I'm doing quite fine. I've tested out several distros, and I have a problem with Ubuntu. Monitor detection. Actually, with Fedora or Knoppix, my IIYama 901HT (Vision Master Pro 450) is fully recognized, thus allowing a refresh rate of 85 Hz @ 1600x1200. However, with ubuntu, I'm stuck @ 60 Hz whatever the resolution.

I have had a look at the Xorg.conf file, and as far as Fedora is concerned, my IIyama is mentioned there, along with its refresh rates, but with Ubuntu,  some kind of generic monitor is mentioned, thus forbidding any higher than 60 Hz refresh rate. I then have copied / pasted the monitor config from fedora to Ubuntu into Xorg.conf, and it seemed to work... OK, but not nice, nor user friendly as Ubuntu shall be.

1st question : Why hasn't it been detected ? My monitor is a well known one... Is hardware detection in the early stages at Ubuntu HQ ?

2nd question : what are the consequences of modifying manually this Xorg.conf file ? For instance, will any further Ubuntu update  erase my modification ? I seem to remember I had to type in a special command to enable that...

Thanks.

---

### Post by tseliot on 2006-08-19
> **Strykaas said:**
> 1st question : Why hasn't it been detected ? My monitor is a well known one... Is hardware detection in the early stages at Ubuntu HQ ?
I have no idea of the reason. My monitor (Acer AL1715) is detected flawlessly.

> **Strykaas said:**
> 2nd question : what are the consequences of modifying manually this Xorg.conf file ? For instance, will any further Ubuntu update  erase my modification ? I seem to remember I had to type in a special command to enable that...

Thanks.
Editing the xorg.conf won't mess up anything (unless you mess it up).

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

P.S. using the search function of the forum wouldn't be a bad idea sometimes ;)

---

### Post by Strykaas on 2006-08-19
Thanks for answering.

1.Isn't there any more convenient way to indicate to Ubuntu which monitor it manages, so that Xorg.conf would be automatically updated ? You know that kind of thing you do in windows... 

2.Is there any means to know if my monitor is depicted in any Ubuntu's hardware database ? 

3.And is there any plan to improve Ubuntu's hardware support/detection in a near future ?

I had used the "search button" as you've mentioned, but found nothing related to bad monitor detection. Xorg.conf tweaking was not really the question here... I am surprised my monitor is not detected. And your Acer does not compare to my monitor in terms of sales... So, a big question mark here.

Regards.

---

### Post by Strykaas on 2008-05-07
TADA !

8.04 came and now everything is correctly detected ! Nice :)

---

