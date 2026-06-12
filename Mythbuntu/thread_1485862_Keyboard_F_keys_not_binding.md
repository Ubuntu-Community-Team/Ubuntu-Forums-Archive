---
title: "Keyboard F keys not binding"
date: 2010-05-17
forum: Mythbuntu
---

### Post by juanfernandes on 2010-05-17
Hi all,

Been signed up for a while but have not been a very active member :confused:

I have searched extensively and have not found an answer for my query.

I have Mythbuntu 9.10.

I have an Acer Revo and it comes with a wireless keyboard. This works. But I want to change some of the key mappings. 

So I went along to **Utilities/Setup > Edit Keys**

I found the Context I want to change and when I press the F key I want to change it, it doesn't recognise that I have pressed it. 

So for example, I want to change the Mute context to F5 (On the keyboard it has a mute sign) but it does nothing when I do so. 

Any ideas why it's not allowing me to use F keys?

Thanks in advance.

Juan

---

### Post by juanfernandes on 2010-05-17
> **juanfernandes said:**
> Hi all,

Been signed up for a while but have not been a very active member :confused:

I have searched extensively and have not found an answer for my query.

I have Mythbuntu 9.10.

I have an Acer Revo and it comes with a wireless keyboard. This works. But I want to change some of the key mappings. 

So I went along to **Utilities/Setup > Edit Keys**

I found the Context I want to change and when I press the F key I want to change it, it doesn't recognise that I have pressed it. 

So for example, I want to change the Mute context to F5 (On the keyboard it has a mute sign) but it does nothing when I do so. 

Any ideas why it's not allowing me to use F keys?

Thanks in advance.

Juan

Don't have access to my media centre right now, so I can't check, but do I just edit the .lirc file? Does this apply if your using a keyboard?

---

### Post by juanfernandes on 2010-05-18
> **juanfernandes said:**
> Don't have access to my media centre right now, so I can't check, but do I just edit the .lirc file? Does this apply if your using a keyboard?

Wow this forum is helpful. 

Did I miss something?? 

Is there a reason I can't use F keys to control actions like MUTE VOLUME UP and DOWN etc. 

Where can I manually edit the key mappings??

Thanks

---

### Post by juanfernandes on 2010-05-26
Bump :(

---

### Post by roger1818 on 2010-05-27
This is a known bug that was fixed in [Ticket #7359]("http://cvs.mythtv.org/trac/ticket/7359").

---

### Post by juanfernandes on 2010-05-27
> **roger1818 said:**
> This is a known bug that was fixed in [Ticket #7359]("http://cvs.mythtv.org/trac/ticket/7359").

Hi Roger

Thanks for the reply. 

Im not sure what I need to do to 'apply' the fix to my mythbuntu. Do I just download this file: [http://cvs.mythtv.org/trac/changeset/22635](http://cvs.mythtv.org/trac/changeset/22635)

Thanks and sorry I'm a n00b!

---

### Post by juanfernandes on 2010-06-10
I have upgraded to the latest version of Mythbuntu and you can now bind F keys.

---

### Post by roger1818 on 2010-06-10
> **juanfernandes said:**
> I have upgraded to the latest version of Mythbuntu and you can now bind F keys.

Nice to know.  I figured as much, but didn't know for sure.  I hope to do the upgrade in the next week or so (rolling in new hardware at the same time).

---

### Post by juanfernandes on 2010-06-10
> **roger1818 said:**
> Nice to know.  I figured as much, but didn't know for sure.  I hope to do the upgrade in the next week or so (rolling in new hardware at the same time).

Does that mean you are going to do a fresh install? I read that most people recomend you don't upgrade, but do a fresh install. 

I couldnt do a fresh install, I upgraded instead, seems to be fine though!

---

### Post by roger1818 on 2010-06-10
> **juanfernandes said:**
> Does that mean you are going to do a fresh install? I read that most people recomend you don't upgrade, but do a fresh install.

Yes.  The only thing that will be the same in both units will be the tuner card so a fresh install is the only way to go.

> I couldnt do a fresh install,

Why couldn't you do a fresh install?

---

