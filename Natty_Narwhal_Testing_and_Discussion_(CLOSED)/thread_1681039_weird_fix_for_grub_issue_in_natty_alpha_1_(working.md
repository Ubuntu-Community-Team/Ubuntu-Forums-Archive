---
title: "weird fix for grub issue in natty alpha 1 (working)"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by xgt001 on 2011-02-03
hey everyone
i think u all are familiar with the ubiquity problem in natty alpha 1 . we needed to instal grub manually, after installation of natty..
but for someone who is not so good at terminal and codes(including me :lolflag:) here is wat i did 
(Intial config
dual boot of Windows 7 on sda5 (logical) and maverick on sda8, sda9 as swap)
1) clean install of natty by formatting maverick partition
2) at the end of install i got the error something like grub install failed ... i selected manually install grub option and rebooted into natty
3) to my wonder sda1 was not at all visible !!! :lolflag: i checked disk utility and it showed that the filesystem type couldnt be detected .. i tried running sudo update-grub but it dint detect win7 partition :(
4) here is the **WEIRDEST** thing i did that worked lol!! i rebooted using Windows Vista DVD (thts rite i dint have a win7 bootable dvd :P) and used the sytem repair option... there i selected startup repair.. it told me to restart .. and i rebooted into natty to my surprise it had detected the sda5 partition!!!:KS then i ran "sudo update-grub" once again and it was working !!! i thus got dual boot with windows 7 back!!! :p 


i hope someone finds it useful.... and would be grateful if someone can tell me  what actually went in the windows vista recovery so that natty detected the partition properly as ntfs :guitar:

---

