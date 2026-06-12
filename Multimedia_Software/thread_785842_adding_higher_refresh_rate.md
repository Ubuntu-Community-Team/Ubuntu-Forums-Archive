---
title: "adding higher refresh rate"
date: 2008-05-07
forum: Multimedia Software
---

### Post by andyrue304 on 2008-05-07
Hello,

I've got Hardy 8.04 and an nVidia 8800 GTS. I've got the 'new' restricted driver and everythings working ok at full resolution and compiz works and stuff. BUT, I can't set the refresh rate on my monitor higher than 52Hz, when I know it can do 75...

Any suggestions?

Cheers

---

### Post by Gru001 on 2008-05-07
It seems that you have the same problem as I do, I just posted a similar thread. For me it is even worse, as I get a bouncing box on the screen that tells me "Input not supported".

Do you happen to know which brand your graphic card is, just curious if it is happening to specific brands.

What might work for you is on the following support page:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Specifically the part where they suggests adding HorizSync          and VertRefresh rates under "Monitor" section.

Do let me know how it goes :)

---

### Post by andyrue304 on 2008-05-07
> **Gru001 said:**
> It seems that you have the same problem as I do, I just posted a similar thread. For me it is even worse, as I get a bouncing box on the screen that tells me "Input not supported".

Do you happen to know which brand your graphic card is, just curious if it is happening to specific brands.

What might work for you is on the following support page:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Specifically the part where they suggests adding HorizSync          and VertRefresh rates under "Monitor" section.

Do let me know how it goes :)

Thanks Gru I'll take a look.

EDIT: Well *that* didn't work!

No change. I think it's a problem with the nVidia Driver as when I disable that I can get 75Hz.

My Gfx Card is an nVidia Geforce 8800 GTS 640 Mb

---

### Post by andyrue304 on 2008-05-07
Ok, I just fixed it. I didn't realise but I didn't have the nvidia-settings installed.

As soon as I got this I was able to set the refresh rate at 75Hz and now the Screen resolution panel displays 78Hz!

Woo!

---

