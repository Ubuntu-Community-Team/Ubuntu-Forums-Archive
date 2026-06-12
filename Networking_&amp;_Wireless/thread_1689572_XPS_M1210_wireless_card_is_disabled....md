---
title: "XPS M1210 wireless card is disabled..."
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by lektrik1 on 2011-02-17
how do i enable the wireless card?  this has happened to me the second time and i have no clue what i did the first time to fix it.

please help a noob:popcorn:

---

### Post by amsterdamharu on 2011-02-17
Is it a usb or pci wireless card, if it's usb please post the output of the following command:
```
sudo lsusb -vv
```if it's pci please post the output of the following command:
```
sudo lspci -vv
```You need to post only the part of your wireless card.

Can you post the output of the following command as well?
```
rfkill list
sudo jockey-text
```If rfkill says it's not installed you can install it with the following command:
```
sudo apt-get install rfkill
```To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

