---
title: "how to enable wireless from console?"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by jt_04 on 2009-03-30
When I login to a virtual terminal (?) through Ctrl+Alt+F5, I cannot access the network.  It gives the error: "connect: Network is unreachable".

How do I enable my wireless connection from a terminal?

also, every time my PC starts, I get the message "Enter password for default keyring to unlock".

How can I make it remember my password?  There is no option for that.  I have looked in System->Prefs->Network Tools.  i recall telling it to "always remember" when I first installed ubuntu, but it obviously is not remembering.

Thanks everyone.

---

### Post by jt_04 on 2009-03-31
anyone?  I know there must be an easy answer.  I'm tired of spending hours researching the simplest question, so I just thought I'd ask the forum.

---

### Post by golliwog on 2009-03-31
Not that I would recommend removing the keyring, but here is the guide to do so.

  [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/")

-g

---

### Post by jt_04 on 2009-03-31
> **golliwog said:**
> Not that I would recommend removing the keyring, but here is the guide to do so.

  [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/")

-g

thanks for the help.  that looks like a possible solution.

really, does anyone else find this silly?  i like the idea of the keyring for protecting passwords for ftp sites or whatever...but having to access the keyring to connect to my wireless (EVERY time i boot up)?  is that a little bit overboard?  

Isn't anyone else bothered by the fact that it prevents you from enabling your network connection from a terminal?  which means that if you reboot your computer remotely, it won't be able to re-connect.  why can't the network manager just remember my wireless key in a safe,secure way and connect automatically?  

I never thought I'd say this, but my wireless manager in windows is actually smart enough to remember my key and connect automatically.  i think i much prefer that behavior (in this one isolated case.  all of cases of windows attempting to be "smart" end in failure).  but is windows really better than ubuntu in this case?

---

### Post by jt_04 on 2009-04-02
bump

does anyone have know how to enable the wireless from a terminal with the X server shutdown?

---

