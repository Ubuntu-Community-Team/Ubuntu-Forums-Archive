---
title: "how does OS X (IE: apple's Unix) implement root?"
date: 2009-01-17
forum: Mac OSX
---

### Post by earthpigg on 2009-01-17
yeah... title says it all.

google results confuse me as (i suppose) they are written from the point of view of a current OS X user... i am a current Ubuntu user, so that is the wrong POV.

from an _**Ubuntu point of view**_, can anyone satisfy my curiosity and tell me how OS X implements the root concept (if it does at all)?

thanks :guitar:

---

### Post by Grant A. on 2009-01-17
erm... su? :-|

---

### Post by earthpigg on 2009-01-17
> **Grant A. said:**
> erm... su? :-|

well, that was easy enough lol.

is it the same as ubuntu? user with admin rights enters password and is temporarily root?

---

### Post by Ocxic on 2009-01-17
yes, same as ubuntu -  enter password for admin tasks, root account disabled

---

### Post by damis648 on 2009-01-17
It works exactly the same:
Root is disabled for GUI login by default, but can be enabled, Same as Ubuntu.
'su' logs into a root shell, same as Ubuntu.
'sudo' gives a user (in the 'admin' group) administrative rights, same as Ubuntu.
there is a graphical sudo also for any GUI application needing root access, same as gksudo.

---

### Post by earthpigg on 2009-01-17
i've never used a mac for more than like 5 minutes (that 5 min was drunk, at a party, changing the song in itunes, and trying to find a terminal to see how similar the commands where :) ), but everything i see/read seems to indicate that the end-user experience is about the same as ubuntu except:

-nothing as awesome as ubuntuforums.org.
-better hardware support.


yes/no?

---

### Post by damis648 on 2009-01-17
I suppose so, sure. The main difference is that OS X has a much greater range of commercial software like Adobe and Microsoft Products.

---

### Post by igknighted on 2009-01-17
> **earthpigg said:**
> i've never used a mac for more than like 5 minutes (that 5 min was drunk, at a party, changing the song in itunes, and trying to find a terminal to see how similar the commands where :) ), but everything i see/read seems to indicate that the end-user experience is about the same as ubuntu except:

-nothing as awesome as ubuntuforums.org.
-better hardware support.


yes/no?

Better hardware support for the 6 models Apple makes, but really poor hardware support for every other computer ever made.

---

### Post by schauerlich on 2009-01-17
OS X is my primary OS. Its sudo policy is basically the same as Ubuntu's, and many of the command are the same. One of the biggest differences is that it's BSD based, so a lot of the differences between Linux and BSD apply to Linux and OS X.

---

### Post by Joeb454 on 2009-01-17
> **EDavidBurg said:**
> OS X is my primary OS. Its sudo policy is basically the same as Ubuntu's, and many of the command are the same. One of the biggest differences is that it's BSD based, so a lot of the differences between Linux and BSD apply to Linux and OS X.

Apart from the first part, this is what I've noticed. I don't think you can enable root logins on the desktop version of OS X, but you can enable it on OS X Server :)

If you install macports you also have an apt-get like feature ;) ```
sudo port install $package
```

Also - moved to Mac OS X forum :)

---

### Post by schauerlich on 2009-01-17
> **Joeb454 said:**
> Apart from the first part, this is what I've noticed. I don't think you can enable root logins on the desktop version of OS X, but you can enable it on OS X Server :)

[http://support.apple.com/kb/HT1528](http://support.apple.com/kb/HT1528)

It's enabled by default on Server, but you can enable it on the consumer version.

---

### Post by 3rdalbum on 2009-01-19
> **earthpigg said:**
> is it the same as ubuntu? user with admin rights enters password and is temporarily root?

Yes, but if you're not in the sudoers file or can't remember your password you can still get to root:

```
osascript -e 'tell application "ARDAgent" to do shell script "whoami"'
```

Replace "whoami" with whatever command you want to run as root.

---

