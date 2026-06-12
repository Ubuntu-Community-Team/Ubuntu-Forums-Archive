---
title: "Convert mov to flv - GUI options??"
date: 2008-01-07
forum: Multimedia Production
---

### Post by pjman on 2008-01-07
I've been using [WinFF]("http://biggmatt.com/winff/") to convert mov files to flv on my Windows laptop which works great. The site for WinFF provides the source and deb file for 32bit architecture. I'm running AMD64 (gutsy) and I can't use this deb file to install. I've searched but can't find AMD64 debs and since this program (at least the windows version) is really slick and easy, I was thinking of trying to compile it from source. WinFF is written in Free Pascal and requires Lazarus to compile it. Lazarus consists of 17 separate debs along with their own dependencies for a complete install. That to me seems like a mess I don't want to get myself into.

Are there any other programs that work as nicely as WinFF to do a simple mov --> flv convert? 

Or how about a AMD64 deb of WinFF? :-)

---

### Post by Creative2 on 2008-01-07
ConverrIT has problem with 64 bit system (because is based on gambas2)

Fuoco Tools i don't know =)...... i am in 32 bit (it's based on kommnander)

try Fuoco tools 
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by eye208 on 2008-01-07
> **pjman said:**
> Lazarus consists of 17 separate debs along with their own dependencies for a complete install. That to me seems like a mess I don't want to get myself into.
Why? Would you install it if the maintainers put everything into one package?

---

### Post by pjman on 2008-01-07
> **eye208 said:**
> Why? Would you install it if the maintainers put everything into one package?

Yup - I probably would. Uninstalling is key to this decision. I'm not a programmer and I rarely compile software so I'd want to uninstall Lazarus to free up space and keep my machine "tidy". 

Here is what I'm thinking -

Uninstalling deb programs that were installed via gdebi are quite easy to uninstall - just find it in Synaptic and remove it. But I've found that if the deb file has dependencies (and gdebi automatically installs these) then the only way (that I know of) to get rid of those dependencies is to have written them down during install and manually uninstall them. Am I wrong on this? Is there another way? If so, that would make me happy :-)

---

### Post by pjman on 2008-01-07
> **Creative2 said:**
> ConverrIT has problem with 64 bit system (because is based on gambas2)

Fuoco Tools i don't know =)...... i am in 32 bit (it's based on kommnander)

try Fuoco tools 
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

I'll give that a try. Thanks!

---

### Post by eye208 on 2008-01-07
> **pjman said:**
> But I've found that if the deb file has dependencies (and gdebi automatically installs these) then the only way (that I know of) to get rid of those dependencies is to have written them down during install and manually uninstall them. Am I wrong on this? Is there another way?
Yes there is. In Synaptic you can filter packages by status (by clicking the "status" button in the lower left of the window). Usually there are only two groups: "installed" and "not installed". But if packages have been installed automatically for dependency resolution and the package that depended on them has been removed, these remaining packages appear in a third group: "installed (autoremove)". If you click on that entry in the filters list, you will see all those packages which are no longer needed, so you can remove them easily.

---

### Post by pjman on 2008-01-09
> **eye208 said:**
> "installed (autoremove)". If you click on that entry in the filters list, you will see all those packages which are no longer needed, so you can remove them easily.

I did not know that. Thank you!

---

