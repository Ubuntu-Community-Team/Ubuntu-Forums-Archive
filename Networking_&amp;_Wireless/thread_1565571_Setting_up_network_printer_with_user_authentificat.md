---
title: "Setting up network printer with user authentification"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by Morgonte on 2010-09-01
My work has got a new Sharp MX-1800N network printer. The setup requires user authentification, one password for printing b&w, another for printing color. 
However when they try to set up my netbook running ubuntu desktop 10.04 they don't get it to prompt for a password, which makes the printer reject the printout. How do you fix this?

---

### Post by Morgonte on 2010-09-07
Bump.

Does anybody know if it is at all possible to set up a network printer with user authentification in Lucid? If it's not possible there's no meaning in trying to get my netbook to do this...

Maybe I'm in the wrong category:confused:? If so, please tell me!

---

### Post by jimjohnsean on 2010-09-07
How is the printer set up on your machine? Is it printing to a samba share on another server, or connecting via lpd/ipp directly from your computer to the printer? Which PPD are you using? (I see on the Sharp website there is a Mac PPD for the printer - essentially the Mac print system and the Ubuntu print system are the same, so if you get the right PPD, the printing should work)

---

### Post by Morgonte on 2010-09-07
> **jimjohnsean said:**
> How is the printer set up on your machine? Is it printing to a samba share on another server, or connecting via lpd/ipp directly from your computer to the printer? 

My netbook communicates via wifi through a router to the Sharp machine's printer server. This is no problem, since printing without user authentification works. When user authentification on the Sharp is turned on I don't get Lucid to ask for a user/pwd which is what the printer needs to print.
> **jimjohnsean said:**
> 
Which PPD are you using? (I see on the Sharp website there is a Mac PPD for the printer - essentially the Mac print system and the Ubuntu print system are the same, so if you get the right PPD, the printing should work)
Even better! Sharp provides a linux driver with included PPD file so the PPD should be accurate.

---

### Post by jimjohnsean on 2010-09-07
> **Morgonte said:**
> Even better! Sharp provides a linux driver with included PPD file so the PPD should be accurate.

Okay - that is very good (although, I have a toshiba photocopier, and the Linux PPD they supply with it mangles the user authentication and makes every username = 'CUPS User')

If you open a webbrowser and point it at [http://localhost:631](http://localhost:631), you should be able to see the options enabled in the PPD for the printer. Go to Printers, and beneath the printer name, click "Set Printer Options". Check if there is anything regarding Department Code or User Authentication.

---

### Post by dl_mj12 on 2010-12-20
Did you find a resolution to this?

We are having the same issue within a school, the Windows and Apple drivers supply the option to specify your departmentcode for printing, whereas it is not an option in the linux driver (ppd).

---

