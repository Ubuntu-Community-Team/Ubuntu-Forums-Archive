---
title: "Unable to use Terminal, Synaptic and Ubuntu software center"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by arashiko28 on 2011-04-11
I'm currently working on 11.04 beta 1, with kernel 2.6.38-02063802-generic.

As for today, I find myself unable to update, upgrade, install or remove anything. Since yesterday, I've been experiencing random freezing, specially with low cpu usage activities, such as reading/editing documents or playing videos.

I can't report the bug, because when I try to, there's a message about unknown header/package, therefore, software don't know what to report.

This is from Terminal> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

The attachments shows the error message at synaptic and failed attempt to report, same goes on for Ubuntu Software Center.

---

### Post by sebastian1978 on 2011-04-12
Actually, just fix the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

See [http://ubuntuforums.org/showthread.php?t=863742&highlight=Problem+MergeList](http://ubuntuforums.org/showthread.php?t=863742&highlight=Problem+MergeList)

---

### Post by Grendel336 on 2011-04-12
I had a very similar problem. 

When I first installed 11.04 Beta 1 I was not connected to internet so I clicked off the option to update files during installation. 

I could not use update manager or ubuntu software center without getting similar error messages. 

I reinstalled 11.04 Beta 1 with internet hooked up and with the option of updating files during installation. All my issues with error messages like yours were solved. 

Any chance you installed your beta release like I originally did?

---

