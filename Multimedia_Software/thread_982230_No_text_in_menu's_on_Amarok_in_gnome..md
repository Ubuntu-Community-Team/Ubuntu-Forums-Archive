---
title: "No text in menu's on Amarok in gnome."
date: 2008-11-14
forum: Multimedia Software
---

### Post by dollzii on 2008-11-14
I would really like to use Amarok in Gnome, have done some reading but could not find any solution to my problem. 

I can't see the menu's in Amarok under gnome, even the band-names on the left side is gone.

---

### Post by dollzii on 2008-11-14
I have just discovered that it is the same in every "kde-based" program. Tellico for example. Might there be some kind of font-package that i need to install?

---

### Post by dollzii on 2008-11-14
Just discovered that if I turn off all extra Visual effects, the problem is gone. Anybody know if maybe there is a setting in compiz-config that might help me?

---

### Post by tsardonix on 2008-12-29
Here is a funny thing, I had the same issue with picasa.  so i googled it for picasa this is what they had.

[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/0d7091b2740a6b76/530aba636ec6c96e](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/0d7091b2740a6b76/530aba636ec6c96e)

thanks to anyone who comes up with a solution.  the nvidia trick. not a chance in working causes gnome to reload defaults :oops:

And turning off compiz is a workaround no.. :P

---

### Post by dollzii on 2009-01-08
I solved my problem by reconfiguring the fonts package i had installed.

---

### Post by oliwally on 2009-01-09
> **dollzii said:**
> I solved my problem by reconfiguring the fonts package i had installed.

I have the same problem with amarok. How do you reconfigure the fonts package?

---

### Post by dollzii on 2009-01-11
I did a 

sudo dpkg-reconfigure fontconfig-config

---

### Post by m.chinni on 2009-02-15
Thank you. This solved the problem on my machine.

My choices:
[LIST]
[*][FONT="Courier New"]Font tuning method for screen: Native[/FONT]
[*][FONT="Courier New"]Enable subpixel rendering for screen: Always[/FONT]
[*][FONT="Courier New"]Enable bitmapped fonts by default? Yes[/FONT]
[/LIST]


Massimiliano

---

### Post by kroylar on 2009-03-04
This needs to go in an FAQ or something!  I spent ages trying to figure this out.

Thanks for the solution dollzii.

---

### Post by sasaenator on 2009-04-10
thanx,man!this solved font problem in amarok,but the problem remains in open office 2.4!

---

