---
title: "Need some help configuring horizontal display on my notebook vga output"
date: 2010-07-02
forum: Multimedia Software
---

### Post by morph_89 on 2010-07-02
Hello, here is the thing, when i use the vga output with my user on ubuntu lucid 10.04 with latest stable kernel image the screen is not well placed horizontally. I generated a xorg.conf, i tried a few things but didn't have any luck yet.

the funny part is that if i stop gdm and run startx from root the screen fits perfectly. Now if i do the same process with my user instead of root it doesn't. Could it be a bug in gdm?

I realised this after i made the xorg.conf file. So my first guess was, since that file was a root file, that it if i config my user with that file it will run correctly. I was wrong. The display remained the same.

Another difference between my user and the root user is that i have compiz fusion running as well, could this be the cause of my problem?

I'm attaching my Xorg.0.log; I also copied the same file when i run x from my user, though I'm not really sure wether if it is the same file or not or if it's relevant; I'm attaching the user's log as Xorg.01.log; and also the xorg.conf.new

My other doubt is that if i start X doing startx it doesn't state using xorg.conf.new, whereas if I start it by doing /etc/init.d/gdm start it does; i don't know if this is of any relevance.

My video card is an onboard intel 945GM

Any help would be appreciated, and if anyone want's me to post any information i will also provide it, i put everything i thought it was relevant, but since i don't understand as much as many of you do i might have missed something important.

I used the vga output a lot in my house and i would really like to fit perfectly without running X as root, because as i understand this isn't a very secure option for everyday usage.

Thanks in advance!!

---

### Post by morph_89 on 2010-07-06
bump

---

