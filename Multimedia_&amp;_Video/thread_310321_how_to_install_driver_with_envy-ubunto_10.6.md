---
title: "how to install driver with envy-ubunto 10.6"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by broekskw on 2006-12-01
hi all have been reading for some time and trying to install a nvidia gx5200 driver. tried so many setups with not luck(can not follow all direction as do not understand how to follow them) so cam across this on [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) but still not sure how it works

) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)

3) Log in (if required)

4) Run "envy" by opening Terminal or Konsole and typing (quite obviously):

envy

5) Choose to install or uninstall the driver (from the textual interface)

ok ctrl+alt+f1 get me to a diff screen,i log in and then???? what and how do i open terminal or konsole , after i open them(terminal or konsole) do i just type  envy and then the drivers install, also how di i get back to my desktop screen,is there commands to get back

sorry but have been at this for some time and getting angry](*,) 

thanks hope someone is kind and will help:-D

---

### Post by kvonb on 2006-12-01
Hi,

Firstly, CTRL ALT F7 will get you back to the desktop.

When you are at the terminal (CRTL ALT F1), (if the prompt says "login:" then type your username, press enter then type in your password and press enter), otherwise skip to the next bit.

OK now your logged in, you need to change to the folder where you saved the "envy" script to,  if it was downloaded to your desktop then type the following: (remember that Linux is case sensitive so copy exactly)

```
cd ~/Desktop
```

If you can't remember where you saved it, then type:

```
cd ~
find . -name envy
```

You might need to make the "envy" script executable, do this:

```
chmod +x envy

```

..and finally:

```
./envy
```

Hope that helps :)

---

### Post by broekskw on 2006-12-01
thanks kvonb for your help.tried your way and keep getting some error or file not found, so just typed envy and hit enter and everything worked out ok, driver installed and working.do not now how come it worked this time and not the other times, thanks for the command alt+ctrl+f7 to get me out of that window and back to my desktop.
very new to ubunto but keep trying to lurn everything i can. again thanks for your help:p

---

### Post by kvonb on 2006-12-01
Glad it worked :D.

Hang in there, once you've got the hang of the basics you'll wonder why you didn't switch earlier.  Go Windows cold turkey for a few months and it will feel strange when you boot Windows!

All the best, KEv :)

---

