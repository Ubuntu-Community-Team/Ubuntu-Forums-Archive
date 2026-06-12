---
title: "Nvidia 100.14.11 x server error"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by fremmus on 2007-07-26
ok, so stupid me decided to install Nvidia 100.14.11
i stopped xserver, proceeded to install, got error saying that kernel wasnt found or something like that... than after restarting i get blue screen saying that x server could not be started... i can get exact errors if needed
anyone has any suggestions on what to do?
btw im new to linux world, but i know a thing or two....
before that everything was working just perfect untill this stupid driver :(

please help me [-o<

i tried using search but whatever i found didnt help me

---

### Post by dabl on 2007-07-26
Assuming you'd be a lot more comfortable with any GUI, go to your text prompt, log in, and follow this:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)


Then, to make life easier (I hope) on yourself, download and install the Envy script installer for the Nvidia Driver from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want to download the file "envy_0.9.6-0ubuntu2_all.deb" which is roughly halfway down the page.  Save it to your desktop, right-click it, and then choose "Open with Gdebi Installer" and install it.  Upon completion, Envy will appear in your Applications>System Tools folder, and you can click it to run it.  It will install the new Nvidia driver that you need.

If for any reason the GUI version of the Envy installer fails, you can run it in text mode with ```
sudo envy -t
```

You'll need to remember that after the next kernel upgrade, which will break the driver installation and require you to run envy from the text prompt.

HTH  :guitar:

---

### Post by fremmus on 2007-07-26
thanks for your quick reply

i followed directions from kubuntuforums but after "startx" i just get black screen with blinking warning that monitor will be shut now...


any ideas?

thanks

---

### Post by fremmus on 2007-07-26
allright i got it work

for anyone who runs into the same problem here's wht i did:

1. i downloaded [http://www.fs-driver.org/download/Ext2IFS_1_10c.exe](http://www.fs-driver.org/download/Ext2IFS_1_10c.exe)
2. downloaded envy [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb)
3. using ext2ifs i moved envy to linux partiton into Desktop folder...
3. restart into linux
4. in command line i typed sudo apt-get install -f
than cd Desktop
sudo dpkg -i envy*.deb
and finally sudp envy -t

remove nvidia driver & reinstall it


:)

feeelsss good to be back

---

