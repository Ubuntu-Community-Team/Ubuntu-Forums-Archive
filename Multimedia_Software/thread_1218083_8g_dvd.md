---
title: "8g dvd?"
date: 2009-07-20
forum: Multimedia Software
---

### Post by DGeeez on 2009-07-20
Brasero (default app with Jaunty) won't recognize my 8G DVD+R media at all, and GnomeBaker, which is kinda flaky anyway, doesn't state why, but won't burn to these either. My DVD recorder is stock with my Acer Aspire, and about 18 months old - is "double-layered" DVD that new that it could be my hardware, or is a driver upgrade available to fix the problem?

---

### Post by wizard10000 on 2009-07-20
> **DGeeez said:**
> Brasero (default app with Jaunty) won't recognize my 8G DVD+R media at all, and GnomeBaker, which is kinda flaky anyway, doesn't state why, but won't burn to these either. My DVD recorder is stock with my Acer Aspire, and about 18 months old - is "double-layered" DVD that new that it could be my hardware, or is a driver upgrade available to fix the problem?

Dual layer DVDs require a burner that'll burn DL media.  My guess is your recorder isn't a DL recorder and if that's the case no driver will fix it.

---

### Post by LowSky on 2009-07-20
Double layer/dual layer/ 8GB DVD-RW are the same thing and has been around for years, but it doesn't mean you can burn to that type of media.

Several things can be the issue. Some discs dont work well in some recorders, Acer could have some some cash and not included a device that can do that, or it is software based.

If we knew what model Acer you had we could possilby tell you if the machine can even use those discs

---

### Post by DGeeez on 2009-07-20
> **LowSky said:**
> Double layer/dual layer/ 8GB DVD-RW are the same thing and has been around for years, but it doesn't mean you can burn to that type of media.

Several things can be the issue. Some discs dont work well in some recorders, Acer could have some some cash and not included a device that can do that, or it is software based.

If we knew what model Acer you had we could possilby tell you if the machine can even use those discs

It's the Aspire M5100.

---

### Post by wizard10000 on 2009-07-20
> **DGeeez said:**
> It's the Aspire M5100.

OEM drive is an LG GSA-H41N (Hitachi makes it) and from what I can tell it is indeed a DL burner.

---

### Post by DGeeez on 2009-07-20
> **wizard10000 said:**
> OEM drive is an LG GSA-H41N (Hitachi makes it) and from what I can tell it is indeed a DL burner.

That may be the DVD unit for the Acer M5100 sold 18 months after I bought mine (and then I bought mine from Circuit City before they announced bankruptcy, so it may have been altered by those crooks **sigh**)

The DVD product listed by lshw is DVD RW AD-7170S, the vendor is Optiarc.

---

### Post by mc4man on 2009-07-21
Circuit city wouldn't 'alter' drives, pc manufacturers use different vendors based on price and availability

The Optiarc. is a sony/nec drive and should have dl capabilities.

While i have wine installed solely to use Imgburn you may find k3b able to handle dl iso creation and burns

Some brands of dl media can cause issues, verbatim is the best available and +r is highly preferred over -r (and verbatim dl media 'made in singapore' are the best verbatim dl media

---

### Post by cariboo on 2009-07-21
I have no problem burning dual-layer dvds using brasero in Januty

---

### Post by philcamlin on 2009-07-21
> **cariboo907 said:**
> I have no problem burning dual-layer dvds using brasero in Januty

same here no issues at all

---

### Post by zodiac09 on 2009-07-30
i have the same problem. MY drive is Optiarc DVD RW AD-7560a. It is does support DVD+R DL. I have burnt them under vista. it picks up the discs fine and burns them. I am still looking into this. i can't find much out though. will keep looking though

---

### Post by zodiac09 on 2009-07-30
Although i think that might be my problem. after doing a sudo lshw it said my dvd drives capabilites is:

capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

but i have burnt dvd+DL and read them with this laptop under windows vista. now  i need to find out if i can change that somehow
if at all. but its an OEM version , and i think that is where the proble lies

---

