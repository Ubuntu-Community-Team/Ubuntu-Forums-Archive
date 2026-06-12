---
title: "will ATI cards ever work on ubuntu?"
date: 2009-07-06
forum: Multimedia Software
---

### Post by h2z on 2009-07-06
I've reinstalled ubuntu jaunty 15 times over the past couple of days while trying to get a fully working ATI driver for my Sapphire Radeon 2900GT. In most cases I get "aticonfig: No supported adapters detected" and in some cases I cant even load X. I've tried it "the ubuntu way", Envy (seems as the most stable solution: I can enable desktop effects but can't load "display" in less than 5 minutes) and manual install from ATI.com with no luck. One would think a 2 year old computer would be able to run without any hickups these days. This is getting very frustrating :(

---

### Post by 5nak3 on 2009-07-06
Not sure about your card in particular, but did you check the Jaunty release notes? I remember when it was first released a some cards were listed as not working, or likely to cause problems. 
And others were completely dropped from support of anything other than the open source driver.

---Slightly off topic---

I'm just wondering, is it the same across all Linux distributions or is it just an ubuntu problem with the ATI drivers?

---Back on topic---

---

### Post by automaton26 on 2009-07-06
Sounds like the ATI drivers *should* still work for your card:

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

I install (for my 4850) like this:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

---

### Post by h2z on 2009-07-07
I install (for my 4850) like this:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")[/QUOTE]


I've tried that same method, but I keep getting:

```

sudo aticonfig --initial
aticonfig: No supported adapters detected

```

---

### Post by networm1230 on 2009-07-07
I have a ATI HD 2400 pci card and it work fine with compiz. I just installed the restricted drives for it and it work fine for me. I can change some gpu setting but not all like in windows vista.

---

