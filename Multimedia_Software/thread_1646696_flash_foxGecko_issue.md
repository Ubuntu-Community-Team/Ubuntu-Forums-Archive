---
title: "flash *fox/Gecko issue"
date: 2010-12-16
forum: Multimedia Software
---

### Post by medusa~ on 2010-12-16
Issue:
-------
I was using flash well till of recent. I didn't do any upgrade. flash just started going blank on me.

When I play flash videos from some sites, it shows blank but it's streaming and I can hear the audio and my flashgot(firefox plugin) can detect flash stream. If I want to, I can download it and watch on multimedia player on desktop. This is just on some sites!

To make it more complicated, example, youtube has this problem, but when I play youtube videos say linked on facebook, it displays normal. Strange huh!

I got the FLASH AID plugin to see if my configuration was wrong, it was no go. Everything so far says its ok. but flash plays on some site and don't on some. 

And flash works perfect in chromium browser. So must be *fox/Gecko Engine issue. Below are my system info!

System Info:
-------------
compiz == yes
gdm == gnome
rgba == yes /* the most recent upgrade I did */

ubuntu{ 
    version(10.10 aka maverick meerkat)
}

Video_Card_Driver{
    card(Nvidia GeForce 210)
    driverVersion(260.19.26) /* Proprietory */
}

Browser{ /* main browser: swiftfox*/
    firefox(Ver. 3.6.13);
    swiftfox(Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.12) Gecko/20101107 Firefox/3.6.12);
    
    chromium(8.0.552.215 (67652)); /* flash is complete working here! but I love my Gecko engines. */
}

BrowserPlugins{
    adblock plus
    adblock plus filter uploader
    autofill forms
    autoPager
    BetterPrivacy
    Download Statusbar
    DownThemAll
    DownThemAll AntiContainer
    facebookchatbar
    facebook chat history manager
    FLASH-AID
    flashblock
    flashgot
    greasemonkey /* didnt install any script yet*/
    resurrect pages
    skipscreen
    stumbleUpon
    ubuntu firefox Modifications
    Webmail notifier
    xmarks
}

flash{ 
    player(Shockwave Flash 10.1 r102);
} 

uname{
    all(Linux medusa-lnx 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux);
}

---

### Post by medusa~ on 2010-12-16
Alright, guys, rgba was the culprit! I think this 'thing' is still very experimental and I really found no real usefulness of it cos windows transparencies where overlapping really bad.

I removed it and it knocked my x. When I wanna log in it tries and crashed X and loop back to login screen. And even affected some application like guayadeque, etc.

Summary:
I restored my Clonezilla image of 'before-rgba' and everything is back to normal. To me this package is a very uncontrollable experiment so far. Just avoid it just yet.

---

