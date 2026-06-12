---
title: "Ubuntu terminal is blank and doesn't respond to commands !!!"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by johnyrkj on 2010-06-09
Hi,
			 		   		 		 		I've a very  strange problem with my terminal. Once opened I get a fully  blank  terminal with only the blingking console....not even the  uname/hostname  is there...its absolutely emply and the cursor blinks in  the very  first pixel....And on the top of that it doesn't respond to   commands.....for example typing pwd and enter will just get the letter   pwd typed and cursor goes to the next line...that is the terminal just   looks like an editor...i've tried with alt-f2 to invoke xterm....even   xterm has the same problem....Does anyone has a solution to this   problem....I'm totlally in fix and unable to proceed....I would greatly   appreciate a reply.
Thanks

---

### Post by VastOne on 2010-06-13
> **johnyrkj said:**
> Hi,
			 		   		 		 		I've a very  strange problem with my terminal. Once opened I get a fully  blank  terminal with only the blingking console....not even the  uname/hostname  is there...its absolutely emply and the cursor blinks in  the very  first pixel....And on the top of that it doesn't respond to   commands.....for example typing pwd and enter will just get the letter   pwd typed and cursor goes to the next line...that is the terminal just   looks like an editor...i've tried with alt-f2 to invoke xterm....even   xterm has the same problem....Does anyone has a solution to this   problem....I'm totlally in fix and unable to proceed....I would greatly   appreciate a reply.
Thanks

I have this same issue.  I cannot drop to xterm on a safe boot either and and ctrl alt fn gives me just a blank screen.

I seem to recall reading somewhere that it may be due to how grub 2 handles any boot splash screens which I have loaded..Will check into it further but I too am looking for a resolution.

---

### Post by ranch hand on 2010-06-13
While I doubt the boot splash theory it should be easy to test.

When your menu comes up, hit e.  Edit out the "splash" instruction.  Hit Ctrl+x to boot.

---

### Post by VastOne on 2010-06-13
> **ranch hand said:**
> While I doubt the boot splash theory it should be easy to test.

When your menu comes up, hit e.  Edit out the "splash" instruction.  Hit Ctrl+x to boot.

Had already done that ranch hand, thanks...I loaded a deb (dpkg) (ubuntu-splash-image) that seems to have been the catalyst for this but  cannot confirm until I remove it, which is proving tricky when I try the -r command I am being told it is not in use.

Ironically, I was looking to pick your brain a little later because I am trying to get the fn keys working so that I can work on the nVidia driver issues in 2.6.35 -rc3 kernel I just compiled...

Will let you know the results

Thanks  :KS

---

### Post by ranch hand on 2010-06-13
We just got our first laptop in February and my wife is the one that uses it.  I am aware of the fn key and some of the things you do with it but very vaguely.

Wouldn't take long to pick my brains on that.  The main response I have when reading about it is "huh?" and "wtf".  Took 2 days to figure out how to use the wifi on the Sys76 Pangolin (fn+F11 no physical switch) and that was only after I called them to ask.  I are ignernt on them there laptops (more so even than normal).

You could just go into nautilus and delete the bugger or, maybe better, rename it to see if that is the problem.

---

### Post by VastOne on 2010-06-13
> **ranch hand said:**
> We just got our first laptop in February and my wife is the one that uses it.  I am aware of the fn key and some of the things you do with it but very vaguely.

Wouldn't take long to pick my brains on that.  The main response I have when reading about it is "huh?" and "wtf".  Took 2 days to figure out how to use the wifi on the Sys76 Pangolin (fn+F11 no physical switch) and that was only after I called them to ask.  I are ignernt on them there laptops (more so even than normal).

You could just go into nautilus and delete the bugger or, maybe better, rename it to see if that is the problem.

yep, been there for that one too and it appears, you are right, my theory on it is wrong.

Still a bugger not been able to get to xterm...will continue to research

Thanks

---

### Post by vigstrom on 2010-06-13
Just got to ask a control question, have you checked .bashrc and .profile? ... there's a bash.bashrc in /etc also

---

### Post by VastOne on 2010-06-13
> **vigstrom said:**
> Just got to ask a control question, have you checked .bashrc and .profile? ... there's a bash.bashrc in /etc also

yes, all present, correct and accounted for.  Thanks

---

### Post by seeker5528 on 2010-06-14
> **VastOne said:**
> I have this same issue.  I cannot drop to xterm on a safe boot either and and ctrl alt fn gives me just a blank screen.

Don't know what might cause issues in the xterm. It kinda makes the following seem unlikely, but a couple of things I can think of....

When you install multiple display managers in Ubuntu there can some times be a situation where one starts on the normal VT 7 and the other on VT 1, in which cases switching to one of VT 2-6 should work and terminal windows should function normally. In this situation for each installed display manager you should be able to type 'sudo dpkg-reconfigure display-manager' where 'display-manager' is the package name of an installed display manager. 

Second, if you have a KMS enabled driver and there is a problem with it, there can be some strange symptoms. In the grub boot menu, if you hit 'E' then add 'nomodeset' to the boot options it should disable KMS for that boot. 

Later, Seeker

---

### Post by VastOne on 2010-06-14
> **seeker5528 said:**
> Don't know what might cause issues in the xterm. It kinda makes the following seem unlikely, but a couple of things I can think of....

When you install multiple display managers in Ubuntu there can some times be a situation where one starts on the normal VT 7 and the other on VT 1, in which cases switching to one of VT 2-6 should work and terminal windows should function normally. In this situation for each installed display manager you should be able to type 'sudo dpkg-reconfigure display-manager' where 'display-manager' is the package name of an installed display manager. 

Second, if you have a KMS enabled driver and there is a problem with it, there can be some strange symptoms. In the grub boot menu, if you hit 'E' then add 'nomodeset' to the boot options it should disable KMS for that boot. 

Later, Seeker

Appreciate the feedback Seeker... I had already added and removed the nomodeset without success

I ended up borking my system doing kernel 2.6.35 rc3 testing and ended up reinstalling Lucid and now the issue is resolved.  It was definitely something I did but I was never able to trace it down

It also was not affecting the login to xterm but even from within there I could not get gdm to stop

---

