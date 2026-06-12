---
title: "I med&#347;sed up with Graphic driver and can not boot"
date: 2013-09-14
forum: Multimedia Software
---

### Post by surati on 2013-09-14
Hi
In attempt to solve the standby problem, which apeard after an Update, I messed up with the graphic driver and now I can start Ubuntu only with the text mode and I don´t know how to get back to the graphic layout.
I&#7743; using a Laptop with ubuntu 12. (the latest updated LTS version, I dont remember which one it is...) with 64bit. After the update, the Laptop mostly did not wake up from a standby modus and I could reboot only manually (with the power buttom), anyway ,in order to repair that I followed a tutorial for reinstalling the Graphic driver and since that I cant boot anymore into the normal ubuntu layout.
I have a Ati driver and this is the comand which I used:  sudo -s; apt-get update; apt-get install fglrx-amdcccle-updates -y
How can I fix it back so I can normaly boot into Ubuntu??

---

### Post by surati on 2013-09-14
I removed the graphic driver and the boot-problem was solved (after a few hours) [as a newbie the smallest problem here is like climbing the Himalaya mountains].
Here is how I removed it:

[COLOR=#c20cb9]**dpkg**[/COLOR] [COLOR=#660033]-l[/COLOR] [COLOR=#000000]**|**[/COLOR][COLOR=#c20cb9]**grep**[/COLOR] fglrx     [COLOR=#666666][I]     #show the installed fglrx packages
[/I][/COLOR][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get purge**[/COLOR] fglrx[COLOR=#000000]***    **[/COLOR][COLOR=#666666]*#remove packages*[/COLOR][COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**apt-get autoremove**[/COLOR] [COLOR=#660033]--purge     [/COLOR][COLOR=#666666]*#*[/COLOR][COLOR=#666666][I][COLOR=#666666][I][COLOR=#666666][I]a complete removal
[/I][/COLOR][/I][/COLOR][/I][/COLOR][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]X11[COLOR=#000000]**/**[/COLOR]xorg.conf           [COLOR=#666666][I][COLOR=#666666][I]#remove configuration files
[/I][/COLOR][/I][/COLOR][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]X11[COLOR=#000000]**/**[/COLOR]xorg.conf.failsafe      [COLOR=#666666]*[COLOR=#666666][I]#remove the fallback configuration, in case exists*[/COLOR][/I][/COLOR]

---

