---
title: "Java questions"
date: 2015-01-12
forum: Multimedia Software
---

### Post by charleswb on 2015-01-12
For Ubuntu 14.04 LTS[INDENT]
A) How necessary is Java for functional web browsing? Would I miss it much if I didn't install it?

    B) How much of a security risk is Java? Does it make me vulnerable to viruses or other security threats? If so, is it a minor risk or a serious risk? Is it really worth enabling Java?

    C) Is Java repository(ies) installed and enabled by default?

    D) Are Java packages installed and enabled by default? If so, which ones?

    E) If I wanted to install Java repositories, which of the following 3 is best method?
[/INDENT]
[INDENT=2]
1) Go to System Settings>>Ubuntu Software window>>Ubuntu Software tab, then check/enable "restricted" and "multiverse"

2) Go to System Settings>>Ubuntu Software window>>Other Software tab, then check/enable "Canonical Partners" and "Independent"

3) In a terminal window run this: sudo add-apt-repository -y ppa:webupd8team/java && sudo apt-get install openjdk-7-jre oracle-java8-installer
[/INDENT]
[INDENT]
    F) Does Firefox or Chrome come with a Java plugin enabled by default?

    G) If I need a Java plugin for Firefox or Chrome, do I need to open a terminal window and run this?  sudo apt-get install icedtea-7-plugin
[/INDENT]

---

### Post by Yellow Pasque on 2015-01-12
> **charleswb said:**
>  How necessary is Java for functional web browsing? Would I miss it much if I didn't install it?
It depends on what sites you use. I haven't had it installed in a while and I don't notice a difference.

> How much of a security risk is Java? Does it make me vulnerable to viruses or other security threats? If so, is it a minor risk or a serious risk? Is it really worth enabling Java?
It's a risk, just like Flash. You can minimize the risk by keeping your version updated and keeping the plugin disabled by default, using it only on sites where it's needed.

> Is Java repository(ies) installed and enabled by default?
Are Java packages installed and enabled by default? If so, which ones?
If I wanted to install Java repositories, which of the following 3 is best method?
A lot of that is answered here on this (somewhat outdated) page: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
As far as the "best" method, that depends on whether you want to use openjdk or the proprietary Oracle version. I think I'd only bother with the proprietary version if a Java program/site I was using didn't work with openjdk.

> Does Firefox or Chrome come with a Java plugin enabled by default?
No.

> If I need a Java plugin for Firefox or Chrome, do I need to open a terminal window and run this?  sudo apt-get install icedtea-7-plugin
That's the easiest way and it will work for Firefox. Chrome/chromium dropped support for icedtea in version 35.x because Google only wants to use its own plugin API (PPAPI) and icedtea has not been ported to it.

---

### Post by charleswb on 2015-01-20
Anyone else? bump

---

### Post by QIII on 2015-01-20
Which part of your post was not answered to your satisfaction?

---

