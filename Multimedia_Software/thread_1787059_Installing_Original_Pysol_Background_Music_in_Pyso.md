---
title: "Installing Original Pysol Background Music in PysolFC!"
date: 2011-06-20
forum: Multimedia Software
---

### Post by TFrog on 2011-06-20
Everyone by now knows how to install their own music files into PysolFC.  However, for those that want to have the original Pysol background music files in the PysolFC edition, there hasn't been anything said.  Personally, I loved the original background music, so I went to the trouble of figuring out how to get it in PysolFC.  The steps are as follows for those interested.

1.) Download a copy of the original Pysol music deb file from the Ubuntu Hardy repository.  DO NOT INSTALL IT AS NORMAL VIA SYNAPTIC OR WITH GDEBI!!!

2.) Extract the files from the deb file with the command:

    ar vx mypackage.deb  (where mypackage.deb is the package you downloaded)

3.) Now extract the files from the data.tar.gz file with the following command:

    tar -xzvf data.tar.gz or use file roller or in the case of Kubuntu use Ark.

4.) Find the following files and paste them into /home/<username>/.pysolfc/music:

    Astral_Dreams.it
    Bye_For_Now.s3m
    Past_and_Future.it
    Ranger_Song.s3m
    Subsequential.mod

5.) Play PysolFC as you would the original and have fun!

---

