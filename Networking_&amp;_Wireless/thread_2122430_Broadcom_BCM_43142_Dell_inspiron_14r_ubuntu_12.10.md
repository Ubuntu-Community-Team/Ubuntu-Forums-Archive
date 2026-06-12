---
title: "Broadcom BCM 43142/ Dell inspiron 14r/ ubuntu 12.10"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by dranzer19 on 2013-03-05
hello,
i had bought this system in october 2012. when i installed ubuntu 12.10 on it, the wifi wouldn't connect. after searching for a long time on different forums, i came across a solution to the problem which involved installing some packages developed by the answerer.
it worked alright, but now I am having problems with upgrading software and downloading some new software from the internet. (i had downloaded softwares before too, the problem has come up recently)

in particular, when i tried to install OCaml on my laptop, these errors came up:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-base-nox_3.12.1-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-base-nox_3.12.1-2ubuntu3_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libtinfo-dev_5.9-10ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libtinfo-dev_5.9-10ubuntu1_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.9-10ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.9-10ubuntu1_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-interp_3.12.1-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-interp_3.12.1-2ubuntu3_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-nox_3.12.1-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-nox_3.12.1-2ubuntu3_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/camlp4_3.12.1-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/camlp4_3.12.1-2ubuntu3_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/ledit/ledit_2.03-1build2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/ledit/ledit_2.03-1build2_all.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-base_3.12.1-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml-base_3.12.1-2ubuntu3_amd64.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml_3.12.1-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/ocaml/ocaml_3.12.1-2ubuntu3_amd64.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

does anyone know why I am having this problem and how to solve it?

also, till this problem is solved, it would be great if someone could tell me how to download the files required to install OCaml on ubuntu 12.10 on a flash drive (using windows) and then install it on ubuntu?

thanks

---

### Post by chili555 on 2013-03-05
I don't see how this is a wireless card problem. It looks like one of the Ubuntu repositories is faulty right now. I just did, successfully:```
sudo apt-get install ocaml
```When you open Software Sources, where is the repository located? Can you get the software if you change to another, USA, perhaps? Please see attached.

---

