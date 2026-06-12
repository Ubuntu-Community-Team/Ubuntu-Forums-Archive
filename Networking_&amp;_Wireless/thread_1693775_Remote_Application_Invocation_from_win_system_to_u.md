---
title: "Remote Application Invocation from win system to ubuntu"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by mamounjamous on 2011-02-23
I have installed a bioinformatics tool called Pathway Tools on ubuntu 10.10, and I'm trying to access it through ssh client from windows vista client system. my client is puTTY.
I can run the terminal shell, and I log in and everything goes alright. However, when I run the program by typing the following:
./pathway-tools
from the directory of the tool. just like I'm running it from ubuntu directly. I get the following message:
```
aibig@aibig-HP-xw4400-Workstation:~/pathway-tools$ ./pathway-tools
Warning: Constant **&-TAG-MAPPING-LIST** being redefined from
         (("alpha" SYMBOL T "a") ("beta" SYMBOL T "b")
          ("gamma" SYMBOL T "g") ("delta" SYMBOL T "d")
          ("epsilon" SYMBOL T "e") ("zeta" SYMBOL T "z")
          ("eta" SYMBOL T "h") ("theta" SYMBOL T "q")
          ("iota" SYMBOL T "i") ("kappa" SYMBOL T "k")
          ("lambda" SYMBOL T "l") ("mu" SYMBOL T "m")
          ("micro" SYMBOL T "m") ("nu" SYMBOL T "n")
          ("xi" SYMBOL T "x") ("omicron" SYMBOL T "o")
          ("pi" SYMBOL T "p") ("rho" SYMBOL T "r")
          ("sigma" SYMBOL T "s") ("tau" SYMBOL T "t")
          ("upsilon" SYMBOL T "u") ("phi" SYMBOL T "j")
          ("chi" SYMBOL T "c") ("psi" SYMBOL T "y")
          ("omega" SYMBOL T "w") ("Alpha" SYMBOL T "A")
          ("Beta" SYMBOL T "B") ("Gamma" SYMBOL T "G")
          ("Delta" SYMBOL T "D") ("Epsilon" SYMBOL T "E")
          ("Zeta" SYMBOL T "Z") ("Eta" SYMBOL T "H")
          ("Theta" SYMBOL T "Q") ("Iota" SYMBOL T "I")
          ("Kappa" SYMBOL T "K") ("Lambda" SYMBOL T "L")
          ("Mu" SYMBOL T "M") ("Nu" SYMBOL T "N") ("Xi" SYMBOL T "X")
          ("Omicron" SYMBOL T "O") ("Pi" SYMBOL T "P")
          ("Rho" SYMBOL T "R") ("Sigma" SYMBOL T "S")
          ("Tau" SYMBOL T "T") ("Upsilon" SYMBOL T "U")
          ("Phi" SYMBOL T "F") ("Chi" SYMBOL T "C")
          ("Psi" SYMBOL T "Y") ("Omega" SYMBOL T "W")
          ("copy" SYMBOL NIL "&#65533;") ("lt" SYMBOL NIL "<")
          ("gt" SYMBOL NIL ">") ("amp" SYMBOL NIL "&")
          ("quot" SYMBOL NIL "\"") ("reg" SYMBOL NIL "&#65533;")
          ("nbsp" SYMBOL NIL " ") ("deg" SYMBOL NIL "&#65533;")
          ("Aring" SYMBOL NIL "&#1573;") ("dot" SYMBOL NIL "&#65533;")
          ("middot" SYMBOL NIL "&#65533;") ("larr" SYMBOL NIL "<-"))
         to
         (("alpha" SYMBOL T "a") ("beta" SYMBOL T "b")
          ("gamma" SYMBOL T "g") ("delta" SYMBOL T "d")
          ("epsilon" SYMBOL T "e") ("zeta" SYMBOL T "z")
          ("eta" SYMBOL T "h") ("theta" SYMBOL T "q")
          ("iota" SYMBOL T "i") ("kappa" SYMBOL T "k")
          ("lambda" SYMBOL T "l") ("mu" SYMBOL T "m")
          ("micro" SYMBOL T "m") ("nu" SYMBOL T "n")
          ("xi" SYMBOL T "x") ("omicron" SYMBOL T "o")
          ("pi" SYMBOL T "p") ("rho" SYMBOL T "r")
          ("sigma" SYMBOL T "s") ("tau" SYMBOL T "t")
          ("upsilon" SYMBOL T "u") ("phi" SYMBOL T "j")
          ("chi" SYMBOL T "c") ("psi" SYMBOL T "y")
          ("omega" SYMBOL T "w") ("Alpha" SYMBOL T "A")
          ("Beta" SYMBOL T "B") ("Gamma" SYMBOL T "G")
          ("Delta" SYMBOL T "D") ("Epsilon" SYMBOL T "E")
          ("Zeta" SYMBOL T "Z") ("Eta" SYMBOL T "H")
          ("Theta" SYMBOL T "Q") ("Iota" SYMBOL T "I")
          ("Kappa" SYMBOL T "K") ("Lambda" SYMBOL T "L")
          ("Mu" SYMBOL T "M") ("Nu" SYMBOL T "N") ("Xi" SYMBOL T "X")
          ("Omicron" SYMBOL T "O") ("Pi" SYMBOL T "P")
          ("Rho" SYMBOL T "R") ("Sigma" SYMBOL T "S")
          ("Tau" SYMBOL T "T") ("Upsilon" SYMBOL T "U")
          ("Phi" SYMBOL T "F") ("Chi" SYMBOL T "C")
          ("Psi" SYMBOL T "Y") ("Omega" SYMBOL T "W")
          ("copy" SYMBOL NIL "&#65533;") ("lt" SYMBOL NIL "<")
          ("gt" SYMBOL NIL ">") ("amp" SYMBOL NIL "&")
          ("quot" SYMBOL NIL "\"") ("reg" SYMBOL NIL "&#65533;")
          ("nbsp" SYMBOL NIL " ") ("emdash" SYMBOL NIL "-")
          ("mdash" SYMBOL NIL "-") ("endash" SYMBOL NIL "-")
          ("prime" SYMBOL NIL "'") ("#8217" SYMBOL NIL "'")
          ("#8242" SYMBOL NIL "'") ("deg" SYMBOL NIL "&#65533;")
          ("Aring" SYMBOL NIL "&#1573;") ("middot" SYMBOL NIL "&#65533;")
          ("larr" SYMBOL NIL "<-") ("rarr" SYMBOL NIL "->")
          ("harr" SYMBOL NIL "<->") ("#8596" SYMBOL NIL "<->")
          ("Acirc" SYMBOL NIL "&#1570;") ("plusmn" SYMBOL NIL "&#65533;")).
Warning: Constant **<-TAG-MAPPING-LIST** being redefined from
         (("I" ITALIC T) ("B" BOLD T) ("EM" ITALIC T) ("SUP" SUP T)
          ("SUB" SUB T) ("U" UNDERL T) ("GREEK" SYMBOL T)
          ("SYMBOL" SYMBOL T) ("/EM" ITALIC NIL) ("/I" ITALIC NIL)
          ("/B" BOLD NIL) ("/SUP" SUP NIL) ("/SUB" SUB NIL)
          ("/U" UNDERL NIL) ("/GREEK" SYMBOL NIL)
          ("/SYMBOL" SYMBOL NIL) ("CENTER" IGNORE NIL)
          ("/CENTER" IGNORE NIL) ("FONT" IGNORE NIL)
          ("/FONT" IGNORE NIL) ("BR" LINE-BREAK NIL) ("P" IGNORE NIL)
          ("UL" IGNORE NIL) ("/UL" IGNORE NIL) ("LI" IGNORE NIL)
          ("H1" HEADER T) ("H2" HEADER T) ("H3" HEADER T)
          ("/H1" HEADER NIL) ("/H2" HEADER NIL) ("/H3" HEADER NIL)
          ("A" ANCHOR T) ("/A" ANCHOR NIL) ("IMG" IMAGE NIL)
          ("PRE" IGNORE NIL) ("/PRE" IGNORE NIL) ("SPAN" IGNORE NIL)
          ("/SPAN" IGNORE NIL))
         to
         (("I" ITALIC T) ("B" BOLD T) ("EM" ITALIC T) ("SUP" SUP T)
          ("SUB" SUB T) ("U" UNDERL T) ("GREEK" SYMBOL T)
          ("SYMBOL" SYMBOL T) ("/EM" ITALIC NIL) ("/I" ITALIC NIL)
          ("/B" BOLD NIL) ("/SUP" SUP NIL) ("/SUB" SUB NIL)
          ("/U" UNDERL NIL) ("/GREEK" SYMBOL NIL)
          ("/SYMBOL" SYMBOL NIL) ("CENTER" IGNORE NIL)
          ("/CENTER" IGNORE NIL) ("FONT" IGNORE NIL)
          ("/FONT" IGNORE NIL) ("BR" LINE-BREAK NIL) ("P" IGNORE NIL)
          ("UL" IGNORE NIL) ("/UL" IGNORE NIL) ("LI" IGNORE NIL)
          ("H1" HEADER T) ("H2" HEADER T) ("H3" HEADER T)
          ("/H1" HEADER NIL) ("/H2" HEADER NIL) ("/H3" HEADER NIL)
          ("A" ANCHOR T) ("/A" ANCHOR NIL) ("IMG" IMAGE NIL)
          ("PRE" IGNORE NIL) ("/PRE" IGNORE NIL) ("SPAN" IGNORE NIL)
          ("/SPAN" IGNORE NIL) ("SMALL" IGNORE NIL)
          ("/SMALL" IGNORE NIL)).
;; Optimization settings: safety 1, space 1, speed 3, debug 1.
;; For a complete description of all compiler switches given the
;; current optimization settings evaluate (EXPLAIN-COMPILER-SETTINGS).

*** This Pathway Tools executable built on Thu Oct 14, 2010 at 2:22:40. ***

[Processed 375 data rows from file /home/aibig/ptoolsData/ptools-local/ptools-init.dat]
[Reading existing Pathway Tools init file: "/home/aibig/ptoolsData/ptools-local/ptools-init.dat" ]
[Start downloading patches...
If any patches are being installed, they are listed in the terminal window.
Looking for patches in
  http://bioinformatics.ai.sri.com/ptools/14.5/Linux/patches/
No patches need to be installed.
... done downloading patches]
Opening Navigator window.

Enter name of X-window server to connect to (of the form HOST:N.M):

```

You can ignore all the warnings, all my problem is at the last line.
I searched the internet to know what does they mean by HOST:N.M value the shell requests, but in vain.

I'm really a newbie to ubuntu, but I'm getting familiar day by day and I'm loving it. I hope to receive some help from somebody soon. I will appreciate any suggestions.

Thanks.

---

### Post by chili555 on 2011-02-23
I believe it's asking which display you want the graphical user interface (GUI) to appear on, since you didn't issue the command from display:0.0  That is, the Ubuntu machine.

In the Linux world, you can ssh in to the Ubuntu machine and ask it to refer the GUI back to the machine from whence the ssh came like this:```
ssh [COLOR="Red"]-X[/COLOR] 192.168.1.xx
```I suspect it is just as easy from Windows and puTTY. In your case, it will require an X server running on your Windows machine.

We have now exhausted my meager knowledge on this subject and, like many problems in life, it appears that one answer raises three more questions.

---

