---
title: "Fax over IP, HOW?"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by iosifidis on 2009-05-31
Hello,

I just got a service that I can send faxes over the internet. They gave me a username and password. At their site they say to download a windows printer driver and install it. When I open it, I'll put the user/pass they gave me and when I have to fax something, I must send it over IP.

Well I tried to search t38modem but I couldn't figure out how to set up.
I also found the program zoiper that it can be used as voip and foip (fax over ip) but I couldn't understand how (how to set it up).

Can anyone has an idea how to do it?
I asked the company to help me. I don't think they'll find it out.

---

### Post by iosifidis on 2009-10-11
It works (theoretically). All you need are:

1. Install from **Synaptic** the **t38modem**.

2. Download [zoiper](http://www.zoiper.com/). Zoiper is a very small-simple VOIP program. You can download it from the page of [downloads](http://www.zoiper.com/zlinux.php). 
Directly you can download the file [zoiper211-linux.tar.gz](http://www.zoiper.com/downloads/free/linux/zoiper211-linux.tar.gz). 
When you have it, open terminal:

```
tar zxf zoiper211-linux.tar.gz 
```

and run it:

```
./zoiper 
```

it will open the program:

[img]http://diamond.fileave.com/foip/zoiper_screenshot_new3.jpg[/img]

For more information see [Zoiper Free manual](http://www.zoiper.com/downloads/Zoiper_2.0_Free_Manual.pdf).

Press the small key and you'll see the settings. You must register your **VOIP** account.

**HOW I SEND FAX**

1. Save the file as **TIFF**.

2. Open **zoiper** and write the number you want to send it to.

3. Press the icon (see image) that will show you **Send  fax**.

[img]http://diamond.fileave.com/foip/zoiper2zoiperfax.gif[/img]

4. Then find the **TIFF** file.

Send fax. The receiver MUST be able to receive the T38 faxes. Otherwise it will show you "Media not supported".

Sources:
[Zoiper Free manual](http://www.zoiper.com/downloads/Zoiper_2.0_Free_Manual.pdf)
[Sending Fax from Zoiper to Zoiper using T.38](http://www.asteriskguru.com/tutorials/zoiper2zoiperfaxt38.html)

---

### Post by axiatel.com on 2011-04-19
Hi, you don't need to download any program. The fax to email, fax via email, online fax or internet fax, FOIPs **dosn't require** you to download any programme. Just use your email to send faxes, but in a special format for example [EMAIL="6123456789@fax.axiatel.com"][COLOR=#000000]6[/COLOR]123456789@fax.axiatel.com[/EMAIL] , where the number is the fax number that you need to send to and everythuing else is your provider's details. They should also give you access to the interface that you can freely send and receive your digiatl faxes stroing them there if you want to. Try Axiatel for free during first 30 days for comparision, and indeed there is nothing to install!
 
visit: [http://www.axiatel.com/au/en/fax-to-email/](http://www.axiatel.com/au/en/fax-to-email/)

---

### Post by piine on 2011-09-07
I just did a test on your fax to email service and I get an error, can't fax outside the country you're browsing... well, this seems to be an Australian site and I'm in the US, as well, this is a paid service and I'm sure the original poster was looking for something free and open source... if anyone has a free and open source solution, please, let us know...

---

