---
title: "installing wicd without internet"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by miyu123 on 2010-07-05
[FONT=Arial][SIZE=2]I'm new to Linux- I think it's great and it was awesome until my wifi stopped working and I started combing forums in search for help.  So, here I am! Please bear with me- i don't understand Linux well and I need very detailed instructions :)

  
[/SIZE][/FONT][FONT=Arial][SIZE=2]I have a Dell Mini with Unbuntu Hardy 8.04 with a Broadcom STA wireless card BCM4312 802.11b/g. In April the Network Manager stopped working. 
After trying various fixes, based on advice and instructions  posted for others who had the same issue, today I decided to completely uninstall the Network Manager and install wicd- which seems like a working alternative. I uninstalled the Network Manager and used the installation instructions for wicd ([http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) ).  While connected to the internet with a wired connection, in my Synaptic Package Manager I entered the new  address [SIZE=3]deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras.[/SIZE] Then I opened a terminal and entered:

[/SIZE][/FONT][FONT=Arial][SIZE=2]wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

This is what I got:

wget: invalid option --0
[sudo] password for miyu: ( I entered the password)
Usage: apt-key [command] [arguments]" 

Manage apt's list of trusted keys

apt-key add <file>  - add the key contained in <file>('-' for stdin)
apt-key del <keyid> - remove the key <keyid>
apt- key export <keyid>- output the key [/SIZE][/FONT][FONT=Arial][SIZE=2]<keyid>
apt-key export all - output all trusted keys
apt-key update - update keys using the keyring package
apt-key net-update- update keys using the network
apt-key list - list keys

[/SIZE][/FONT][FONT=Arial][SIZE=2]It looks like an argument is needed, but I have no idea how to add that to the command. I've found the key file (I think) here [/SIZE][/FONT][http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg)[FONT=Arial][SIZE=2], but I don't know what to do next.  

Any help is greatly appreciated!
Thank you!
[/SIZE][/FONT]

---

### Post by Revolutionary101 on 2010-07-05
Copy and past this command into terminal: (I know it is the same one but from the error message it looks like you typed --0 somewhere)
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```
After that works then run this command:
```
sudo apt-get install wicd
```

Just ask if you have any questions.

---

### Post by miyu123 on 2010-07-06
> **Revolutionary101 said:**
> Copy and past this command into terminal: (I know it is the same one but from the error message it looks like you typed --0 somewhere)
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```After that works then run this command:
```
sudo apt-get install wicd
```Just ask if you have any questions.

First, Thank you so much for your help! I appreciate it.

I just followed your instructions. I copied the exact command you typed here and pasted into terminal.The error now says[FONT=Microsoft Sans Serif]: 

[FONT=Courier New]gpg: no valid OpenPGP data found[/FONT][/FONT]

I tried that a couple of times, checking the spelling and spacing every time. 

I don't give up easy, so I tried one more time with both commands:

[FONT=Courier New]miyu@miyu: ~$ wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -
[/FONT][FONT=Courier New]gpg: no valid  OpenPGP data found
miyu@miyu:~$
miyu@miyu:~$ sudo apt-get install wicd
[/FONT][FONT=Courier New]Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package wicd

[/FONT] I don't know if this helps. 
Thank you,

---

### Post by Revolutionary101 on 2010-07-06
Haha wow I forgot the name of this thread. That first command I gave you would add the wicd repositories, but it can't reach them because you have no internet.

If you have another computer with internet access go to this website:
[http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)

Then go down wicd-1.7.0.tar.bz2 click on that and download that file to a flash drive or some other removable storage so you can transfer it to the computer with no internet.

Once you get the removable storage into your computer with no internet copy that file to your Home folder. Then you must journey into terminal and type these in:
```
tar -jxvf wicd-1.7.0.tar.bz2
```
That extracts the file to the folder wicd-1.7.0
```
cd wicd-1.7.0
```
That will set the folder that you are in to the one that has all the extracted files in
```
sudo python setup.py configure
```
That configures the install files to be installed
```
sudo python setup.py install
```
Then that will install wicd for you

After you have entered all of those commands then restart your computer to use wicd.

---

### Post by miyu123 on 2010-07-07
> **Revolutionary101 said:**
> Haha wow I forgot the name of this thread. That first command I gave you would add the wicd repositories, but it can't reach them because you have no internet.

If you have another computer with internet access go to this website:
[http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)

Then go down wicd-1.7.0.tar.bz2 click on that and download that file to a flash drive or some other removable storage so you can transfer it to the computer with no internet.

Once you get the removable storage into your computer with no internet copy that file to your Home folder. Then you must journey into terminal and type these in:
```
tar -jxvf wicd-1.7.0.tar.bz2
```
That extracts the file to the folder wicd-1.7.0
```
cd wicd-1.7.0
```
That will set the folder that you are in to the one that has all the extracted files in
```
sudo python setup.py configure
```
That configures the install files to be installed
```
python setup.py install
```
Then that will install wicd for you

After you have entered all of those commands then restart your computer to use wicd.
Thank you for your patience!
Every day I'm one step closer to achieving wireless freedom:) I copied the installation package in the Home folder and ran the commands. It worked for the most part... I have an error at the end of installation saying it couldn't create something.  I'm copying the whole story below...

wicd-1.7.0/translations/et/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/pt/
wicd-1.7.0/translations/pt/LC_MESSAGES/
wicd-1.7.0/translations/pt/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/gl/
wicd-1.7.0/translations/gl/LC_MESSAGES/
wicd-1.7.0/translations/gl/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/it/
wicd-1.7.0/translations/it/LC_MESSAGES/
wicd-1.7.0/translations/it/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/zh_CN/
wicd-1.7.0/translations/zh_CN/LC_MESSAGES/
wicd-1.7.0/translations/zh_CN/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es/
wicd-1.7.0/translations/es/LC_MESSAGES/
wicd-1.7.0/translations/es/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ka/
wicd-1.7.0/translations/ka/LC_MESSAGES/
wicd-1.7.0/translations/ka/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/eu/
wicd-1.7.0/translations/eu/LC_MESSAGES/
wicd-1.7.0/translations/eu/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/en_CA/
wicd-1.7.0/translations/en_CA/LC_MESSAGES/
wicd-1.7.0/translations/en_CA/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/fr_CA/
wicd-1.7.0/translations/fr_CA/LC_MESSAGES/
wicd-1.7.0/translations/fr_CA/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/te/
wicd-1.7.0/translations/te/LC_MESSAGES/
wicd-1.7.0/translations/te/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ar_EG/
wicd-1.7.0/translations/ar_EG/LC_MESSAGES/
wicd-1.7.0/translations/ar_EG/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/sv/
wicd-1.7.0/translations/sv/LC_MESSAGES/
wicd-1.7.0/translations/sv/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/fr_FR/
wicd-1.7.0/translations/fr_FR/LC_MESSAGES/
wicd-1.7.0/translations/fr_FR/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/de/
wicd-1.7.0/translations/de/LC_MESSAGES/
wicd-1.7.0/translations/de/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/hr_HR/
wicd-1.7.0/translations/hr_HR/LC_MESSAGES/
wicd-1.7.0/translations/hr_HR/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/pt_BR/
wicd-1.7.0/translations/pt_BR/LC_MESSAGES/
wicd-1.7.0/translations/pt_BR/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es_ES/
wicd-1.7.0/translations/es_ES/LC_MESSAGES/
wicd-1.7.0/translations/es_ES/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/kk/
wicd-1.7.0/translations/kk/LC_MESSAGES/
wicd-1.7.0/translations/kk/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/fr/
wicd-1.7.0/translations/fr/LC_MESSAGES/
wicd-1.7.0/translations/fr/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/lt/
wicd-1.7.0/translations/lt/LC_MESSAGES/
wicd-1.7.0/translations/lt/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/hu/
wicd-1.7.0/translations/hu/LC_MESSAGES/
wicd-1.7.0/translations/hu/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/cs/
wicd-1.7.0/translations/cs/LC_MESSAGES/
wicd-1.7.0/translations/cs/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ar_PS/
wicd-1.7.0/translations/ar_PS/LC_MESSAGES/
wicd-1.7.0/translations/ar_PS/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/it_IT/
wicd-1.7.0/translations/it_IT/LC_MESSAGES/
wicd-1.7.0/translations/it_IT/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/fi/
wicd-1.7.0/translations/fi/LC_MESSAGES/
wicd-1.7.0/translations/fi/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/el/
wicd-1.7.0/translations/el/LC_MESSAGES/
wicd-1.7.0/translations/el/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/bg/
wicd-1.7.0/translations/bg/LC_MESSAGES/
wicd-1.7.0/translations/bg/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es_CL/
wicd-1.7.0/translations/es_CL/LC_MESSAGES/
wicd-1.7.0/translations/es_CL/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ca/
wicd-1.7.0/translations/ca/LC_MESSAGES/
wicd-1.7.0/translations/ca/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es_VE/
wicd-1.7.0/translations/es_VE/LC_MESSAGES/
wicd-1.7.0/translations/es_VE/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/he/
wicd-1.7.0/translations/he/LC_MESSAGES/
wicd-1.7.0/translations/he/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es_GT/
wicd-1.7.0/translations/es_GT/LC_MESSAGES/
wicd-1.7.0/translations/es_GT/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es_MX/
wicd-1.7.0/translations/es_MX/LC_MESSAGES/
wicd-1.7.0/translations/es_MX/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/lv/
wicd-1.7.0/translations/lv/LC_MESSAGES/
wicd-1.7.0/translations/lv/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ko/
wicd-1.7.0/translations/ko/LC_MESSAGES/
wicd-1.7.0/translations/ko/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/eo/
wicd-1.7.0/translations/eo/LC_MESSAGES/
wicd-1.7.0/translations/eo/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/sk/
wicd-1.7.0/translations/sk/LC_MESSAGES/
wicd-1.7.0/translations/sk/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/es_NI/
wicd-1.7.0/translations/es_NI/LC_MESSAGES/
wicd-1.7.0/translations/es_NI/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/zh_TW/
wicd-1.7.0/translations/zh_TW/LC_MESSAGES/
wicd-1.7.0/translations/zh_TW/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ru_RU/
wicd-1.7.0/translations/ru_RU/LC_MESSAGES/
wicd-1.7.0/translations/ru_RU/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/de_DE/
wicd-1.7.0/translations/de_DE/LC_MESSAGES/
wicd-1.7.0/translations/de_DE/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/pl/
wicd-1.7.0/translations/pl/LC_MESSAGES/
wicd-1.7.0/translations/pl/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/id/
wicd-1.7.0/translations/id/LC_MESSAGES/
wicd-1.7.0/translations/id/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/zh_HK/
wicd-1.7.0/translations/zh_HK/LC_MESSAGES/
wicd-1.7.0/translations/zh_HK/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/sr/
wicd-1.7.0/translations/sr/LC_MESSAGES/
wicd-1.7.0/translations/sr/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ro/
wicd-1.7.0/translations/ro/LC_MESSAGES/
wicd-1.7.0/translations/ro/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/vi/
wicd-1.7.0/translations/vi/LC_MESSAGES/
wicd-1.7.0/translations/vi/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/sl/
wicd-1.7.0/translations/sl/LC_MESSAGES/
wicd-1.7.0/translations/sl/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/uk/
wicd-1.7.0/translations/uk/LC_MESSAGES/
wicd-1.7.0/translations/uk/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ml/
wicd-1.7.0/translations/ml/LC_MESSAGES/
wicd-1.7.0/translations/ml/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ja/
wicd-1.7.0/translations/ja/LC_MESSAGES/
wicd-1.7.0/translations/ja/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/ru/
wicd-1.7.0/translations/ru/LC_MESSAGES/
wicd-1.7.0/translations/ru/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/fa/
wicd-1.7.0/translations/fa/LC_MESSAGES/
wicd-1.7.0/translations/fa/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/nl_NL/
wicd-1.7.0/translations/nl_NL/LC_MESSAGES/
wicd-1.7.0/translations/nl_NL/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/nl/
wicd-1.7.0/translations/nl/LC_MESSAGES/
wicd-1.7.0/translations/nl/LC_MESSAGES/wicd.mo
wicd-1.7.0/translations/tr/
wicd-1.7.0/translations/tr/LC_MESSAGES/
wicd-1.7.0/translations/tr/LC_MESSAGES/wicd.mo
wicd-1.7.0/other/
wicd-1.7.0/other/wicd-gtk.xpm
wicd-1.7.0/other/dhclient.conf.template.default
wicd-1.7.0/other/wicd.desktop
wicd-1.7.0/other/wicd-tray.desktop
wicd-1.7.0/other/.empty_on_purpose
wicd-1.7.0/uninstall.sh
wicd-1.7.0/gtk/
wicd-1.7.0/gtk/gui.py
wicd-1.7.0/gtk/configscript.py
wicd-1.7.0/gtk/netentry.py
wicd-1.7.0/gtk/prefs.py
wicd-1.7.0/gtk/wicd-client.py
wicd-1.7.0/gtk/guiutil.py
wicd-1.7.0/.bzrignore
wicd-1.7.0/vcsinfo.py
wicd-1.7.0/INSTALL
wicd-1.7.0/encryption/
wicd-1.7.0/encryption/templates/
wicd-1.7.0/encryption/templates/eap
wicd-1.7.0/encryption/templates/wep-shared
wicd-1.7.0/encryption/templates/wpa-psk
wicd-1.7.0/encryption/templates/wep-passphrase
wicd-1.7.0/encryption/templates/ttls
wicd-1.7.0/encryption/templates/eap-tls
wicd-1.7.0/encryption/templates/wep-hex
wicd-1.7.0/encryption/templates/peap
wicd-1.7.0/encryption/templates/peap-tkip
wicd-1.7.0/encryption/templates/wpa
wicd-1.7.0/encryption/templates/active
wicd-1.7.0/encryption/templates/leap
wicd-1.7.0/depends/
wicd-1.7.0/depends/python-iwscan/
wicd-1.7.0/depends/python-iwscan/iwlist.py
wicd-1.7.0/depends/python-iwscan/pyiwscan.c
wicd-1.7.0/depends/python-iwscan/debian/
wicd-1.7.0/depends/python-iwscan/debian/compat
wicd-1.7.0/depends/python-iwscan/debian/examples
wicd-1.7.0/depends/python-iwscan/debian/rules
wicd-1.7.0/depends/python-iwscan/debian/changelog
wicd-1.7.0/depends/python-iwscan/debian/copyright
wicd-1.7.0/depends/python-iwscan/debian/control
wicd-1.7.0/depends/python-iwscan/setup.py
wicd-1.7.0/depends/python-iwscan/LICENSE
wicd-1.7.0/depends/python-wpactrl/
wicd-1.7.0/depends/python-wpactrl/wpa_ctrl.c
wicd-1.7.0/depends/python-wpactrl/COPYING
wicd-1.7.0/depends/python-wpactrl/example.py
wicd-1.7.0/depends/python-wpactrl/wpactrl.c
wicd-1.7.0/depends/python-wpactrl/wpa_ctrl.h
wicd-1.7.0/depends/python-wpactrl/README
wicd-1.7.0/depends/python-wpactrl/debian/
wicd-1.7.0/depends/python-wpactrl/debian/compat
wicd-1.7.0/depends/python-wpactrl/debian/examples
wicd-1.7.0/depends/python-wpactrl/debian/rules
wicd-1.7.0/depends/python-wpactrl/debian/changelog
wicd-1.7.0/depends/python-wpactrl/debian/copyright
wicd-1.7.0/depends/python-wpactrl/debian/control
wicd-1.7.0/depends/python-wpactrl/Makefile
wicd-1.7.0/depends/python-wpactrl/setup.py
wicd-1.7.0/images/
wicd-1.7.0/images/receiving-good-signal.png
wicd-1.7.0/images/receiving-low-signal-lock.png
wicd-1.7.0/images/receiving-bad-signal-lock.png
wicd-1.7.0/images/receiving-low-signal.png
wicd-1.7.0/images/idle-bad-signal.png
wicd-1.7.0/images/signal-100.png
wicd-1.7.0/images/transmitting-high-signal.png
wicd-1.7.0/images/signal-50.png
wicd-1.7.0/images/idle-high-signal-lock.png
wicd-1.7.0/images/idle-bad-signal-lock.png
wicd-1.7.0/images/transmitting-low-signal-lock.png
wicd-1.7.0/images/transmitting-high-signal-lock.png
wicd-1.7.0/images/both-high-signal-lock.png
wicd-1.7.0/images/no-signal.png
wicd-1.7.0/images/idle-good-signal.png
wicd-1.7.0/images/wired-gui.svg
wicd-1.7.0/images/idle-low-signal-lock.png
wicd-1.7.0/images/both-good-signal-lock.png
wicd-1.7.0/images/idle-good-signal-lock.png
wicd-1.7.0/images/high-signal.png
wicd-1.7.0/images/receiving-good-signal-lock.png
wicd-1.7.0/images/transmitting-good-signal.png
wicd-1.7.0/images/signal-25.png
wicd-1.7.0/images/both-low-signal.png
wicd-1.7.0/images/bad-signal-lock.png
wicd-1.7.0/images/bad-signal.png
wicd-1.7.0/images/transmitting-good-signal-lock.png
wicd-1.7.0/images/transmitting-low-signal.png
wicd-1.7.0/images/both-high-signal.png
wicd-1.7.0/images/idle-high-signal.png
wicd-1.7.0/images/both-bad-signal-lock.png
wicd-1.7.0/images/good-signal.png
wicd-1.7.0/images/both-low-signal-lock.png
wicd-1.7.0/images/high-signal-lock.png
wicd-1.7.0/images/transmitting-bad-signal-lock.png
wicd-1.7.0/images/receiving-bad-signal.png
wicd-1.7.0/images/signal-75.png
wicd-1.7.0/images/good-signal-lock.png
wicd-1.7.0/images/receiving-high-signal.png
wicd-1.7.0/images/idle-low-signal.png
wicd-1.7.0/images/wired.png
wicd-1.7.0/images/both-good-signal.png
wicd-1.7.0/images/low-signal-lock.png
wicd-1.7.0/images/low-signal.png
wicd-1.7.0/images/receiving-high-signal-lock.png
wicd-1.7.0/images/both-bad-signal.png
wicd-1.7.0/images/transmitting-bad-signal.png
wicd-1.7.0/icons/
wicd-1.7.0/icons/192px/
wicd-1.7.0/icons/192px/wicd-gtk.png
wicd-1.7.0/icons/32px/
wicd-1.7.0/icons/32px/wicd-gtk.png
wicd-1.7.0/icons/96px/
wicd-1.7.0/icons/96px/wicd-gtk.png
wicd-1.7.0/icons/22px/
wicd-1.7.0/icons/22px/wicd-gtk.png
wicd-1.7.0/icons/64px/
wicd-1.7.0/icons/64px/wicd-gtk.png
wicd-1.7.0/icons/scalable/
wicd-1.7.0/icons/scalable/wicd-gtk.svg
wicd-1.7.0/icons/36px/
wicd-1.7.0/icons/36px/wicd-gtk.png
wicd-1.7.0/icons/48px/
wicd-1.7.0/icons/48px/wicd-gtk.png
wicd-1.7.0/icons/24px/
wicd-1.7.0/icons/24px/wicd-gtk.png
wicd-1.7.0/icons/128px/
wicd-1.7.0/icons/128px/wicd-gtk.png
wicd-1.7.0/icons/16px/
wicd-1.7.0/icons/16px/wicd-gtk.png
wicd-1.7.0/icons/72px/
wicd-1.7.0/icons/72px/wicd-gtk.png
wicd-1.7.0/man/
wicd-1.7.0/man/wicd-client.1
wicd-1.7.0/man/nl/
wicd-1.7.0/man/nl/wicd-client.1
wicd-1.7.0/README
wicd-1.7.0/init/
wicd-1.7.0/init/suse/
wicd-1.7.0/init/lunar/
wicd-1.7.0/init/arch/
wicd-1.7.0/init/redhat/
wicd-1.7.0/init/default/
wicd-1.7.0/init/pld/
wicd-1.7.0/init/slackware/
wicd-1.7.0/init/debian/
wicd-1.7.0/init/gentoo/
wicd-1.7.0/cli/
wicd-1.7.0/cli/README.cli
wicd-1.7.0/cli/wicd-cli.py
wicd-1.7.0/in/
wicd-1.7.0/in/init=gentoo=wicd.in
wicd-1.7.0/in/init=default=wicd.in
wicd-1.7.0/in/wicd=wpath.py.in
wicd-1.7.0/in/init=pld=wicd.in
wicd-1.7.0/in/init=suse=wicd.in
wicd-1.7.0/in/init=redhat=wicd.in
wicd-1.7.0/in/man=wicd-wireless-settings.conf.5.in
wicd-1.7.0/in/other=wicd.conf.in
wicd-1.7.0/in/man=wicd-curses.8.in
wicd-1.7.0/in/man=nl=wicd-wireless-settings.conf.5.in
wicd-1.7.0/in/other=91wicd.in
wicd-1.7.0/in/scripts=wicd-curses.in
wicd-1.7.0/in/man=wicd.8.in
wicd-1.7.0/in/init=lunar=wicd.in
wicd-1.7.0/in/man=wicd-wired-settings.conf.5.in
wicd-1.7.0/in/other=WHEREAREMYFILES.in
wicd-1.7.0/in/init=arch=wicd.in
wicd-1.7.0/in/other=50-wicd-suspend.sh.in
wicd-1.7.0/in/scripts=wicd.in
wicd-1.7.0/in/scripts=wicd-cli.in
wicd-1.7.0/in/man=nl=wicd.8.in
wicd-1.7.0/in/other=80-wicd-connect.sh.in
wicd-1.7.0/in/wpath.py.in
wicd-1.7.0/in/man=nl=wicd-wired-settings.conf.5.in
wicd-1.7.0/in/scripts=wicd-gtk.in
wicd-1.7.0/in/init=debian=wicd.in
wicd-1.7.0/in/man=nl=wicd-curses.8.in
wicd-1.7.0/in/scripts=wicd-client.in
wicd-1.7.0/in/init=slackware=rc.wicd.in
wicd-1.7.0/in/man=wicd-manager-settings.conf.5.in
wicd-1.7.0/in/man=wicd-cli.8.in
wicd-1.7.0/in/man=nl=wicd-manager-settings.conf.5.in
wicd-1.7.0/setup.py
wicd-1.7.0/curses/
wicd-1.7.0/curses/curses_misc.py
wicd-1.7.0/curses/wicd-curses.py
wicd-1.7.0/curses/README.curses
wicd-1.7.0/curses/netentry_curses.py
wicd-1.7.0/curses/configscript_curses.py
wicd-1.7.0/curses/prefs_curses.py
wicd-1.7.0/LICENSE
miyu@miyu:~$ cd wicd-1.7.0
miyu@miyu:~/wicd-1.7.0$ 
miyu@miyu:~/wicd-1.7.0$ sudo python setup.py configure
[sudo] password for miyu: 
Error importing wpath.py. You can safely ignore this
message. It is probably because you haven't run python setup.py
configure yet or you are running it for the first time.
Using init file name 'wpath' is not defined
Error setting up data array. This is normal if 
python setup.py configure has not yet been run.
running configure
Distro is: auto
NOTICE: Automatic distro detection found: debian, retrying with that...
Distro is: debian
lib is /usr/lib/wicd/
share is /usr/share/wicd/
etc is /etc/wicd/
scripts is /etc/wicd/scripts/
pixmaps is /usr/share/pixmaps/
images is /usr/share/pixmaps/wicd/
encryption is /etc/wicd/encryption/templates/
bin is /usr/bin/
sbin is /usr/sbin/
backends is /usr/share/wicd/backends/
daemon is /usr/share/wicd/daemon/
curses is /usr/share/wicd/curses/
gtk is /usr/share/wicd/gtk/
cli is /usr/share/wicd/cli/
networks is /var/lib/wicd/configurations/
log is /var/log/wicd/
resume is /etc/acpi/resume.d/
suspend is /etc/acpi/suspend.d/
pmutils is /usr/lib/pm-utils/sleep.d/
dbus is /etc/dbus-1/system.d/
desktop is /usr/share/applications/
icons is /usr/share/icons/hicolor/
translations is /usr/share/locale/
autostart is /etc/xdg/autostart/
varlib is /var/lib/wicd/
init is /etc/init.d/
docdir is /usr/share/doc/wicd/
mandir is /usr/share/man/
kdedir is /usr/share/autostart/
python is /usr/bin/python
pidfile is /var/run/wicd/wicd.pid
initfile is init/debian/wicd
initfilename is wicd
wicdgroup is netdev
distro is debian
loggroup is adm
logperms is 0640
Found switch ('no-install-init', None, 'do not install the init file') False
Found switch ('no-install-man', None, 'do not install the man files') False
Found switch ('no-install-i18n-man', None, 'do not install the translated man files') False
Found switch ('no-install-kde', None, 'do not install the kde autostart file') False
Found switch ('no-install-acpi', None, 'do not install the suspend.d and resume.d acpi scripts') False
Found switch ('no-install-pmutils', None, 'do not install the pm-utils hooks') False
Found switch ('no-install-docs', None, 'do not install the auxiliary documentation') False
Found switch ('no-install-ncurses', None, 'do not install the ncurses client') False
Found switch ('no-install-cli', None, 'do not install the command line executable') False
Found switch ('no-install-gtk', None, 'do not install the gtk client') False
Found switch ('no-use-notifications', None, 'do not ever allow the use of libnotify notifications') False
Replacing values in template files...
Replacing values in wicd=wpath.py.in wicd/wpath.py
Replacing values in other=50-wicd-suspend.sh.in other/50-wicd-suspend.sh
Replacing values in wpath.py.in wpath.py
Replacing values in man=nl=wicd.8.in man/nl/wicd.8
Replacing values in scripts=wicd-client.in (mkdir scripts) scripts/wicd-client
Replacing values in man=nl=wicd-manager-settings.conf.5.in man/nl/wicd-manager-settings.conf.5
Replacing values in init=lunar=wicd.in init/lunar/wicd
Replacing values in man=wicd-wireless-settings.conf.5.in man/wicd-wireless-settings.conf.5
Replacing values in init=redhat=wicd.in init/redhat/wicd
Replacing values in man=wicd-wired-settings.conf.5.in man/wicd-wired-settings.conf.5
Replacing values in init=pld=wicd.in init/pld/wicd
Replacing values in man=nl=wicd-wired-settings.conf.5.in man/nl/wicd-wired-settings.conf.5
Replacing values in init=arch=wicd.in init/arch/wicd
Replacing values in init=gentoo=wicd.in init/gentoo/wicd
Replacing values in other=80-wicd-connect.sh.in other/80-wicd-connect.sh
Replacing values in man=wicd-curses.8.in man/wicd-curses.8
Replacing values in init=debian=wicd.in init/debian/wicd
Replacing values in man=nl=wicd-wireless-settings.conf.5.in man/nl/wicd-wireless-settings.conf.5
Replacing values in other=wicd.conf.in other/wicd.conf
Replacing values in man=nl=wicd-curses.8.in man/nl/wicd-curses.8
Replacing values in init=suse=wicd.in init/suse/wicd
Replacing values in scripts=wicd-cli.in scripts/wicd-cli
Replacing values in init=slackware=rc.wicd.in init/slackware/rc.wicd
Replacing values in scripts=wicd-gtk.in scripts/wicd-gtk
Replacing values in man=wicd.8.in man/wicd.8
Replacing values in other=WHEREAREMYFILES.in other/WHEREAREMYFILES
Replacing values in man=wicd-manager-settings.conf.5.in man/wicd-manager-settings.conf.5
Replacing values in init=default=wicd.in init/default/wicd
Replacing values in other=91wicd.in other/91wicd
Replacing values in man=wicd-cli.8.in man/wicd-cli.8
Replacing values in scripts=wicd.in scripts/wicd
Replacing values in scripts=wicd-curses.in scripts/wicd-curses
miyu@miyu:~/wicd-1.7.0$ python setup.py install
Using init file ('/etc/init.d/', 'init/debian/wicd')
Using pid path wicd.pid
Language support for vi da nl sr id it en_CA eu es_NI he zh_TW ja fi eo hu ko lv sk kk ru sv gl ka bg es_ES zh_HK de_DE es tr fr_FR cs de es_VE ro ml uk nl_NL te lt sl pt_BR fr_CA es_MX et hr_HR es_AR ru_RU zh_CN ar_PS es_CL fr pt no ca ar_EG pl fa el it_IT es_GT
running install
running build
running build_py
creating build
creating build/lib
creating build/lib/wicd
copying wicd/__init__.py -> build/lib/wicd
copying wicd/networking.py -> build/lib/wicd
copying wicd/misc.py -> build/lib/wicd
copying wicd/wnettools.py -> build/lib/wicd
copying wicd/wpath.py -> build/lib/wicd
copying wicd/dbusmanager.py -> build/lib/wicd
copying wicd/logfile.py -> build/lib/wicd
copying wicd/backend.py -> build/lib/wicd
copying wicd/configmanager.py -> build/lib/wicd
copying wicd/translations.py -> build/lib/wicd
running install_lib
creating /usr/lib/python2.5/site-packages/wicd
error: could not create '/usr/lib/python2.5/site-packages/wicd': Permission denied
miyu@miyu:~/wicd-1.7.0$ 
miyu@miyu:~/wicd-1.7.0$

---

### Post by Revolutionary101 on 2010-07-07
Im sorry but I had a bit of a typo with the last command. This is the command to install:
```
sudo python setup.py install
```
To install the program the setup file needs root privilege to install, thus the sudo command.

---

### Post by miyu123 on 2010-07-08
> **Revolutionary101 said:**
> Im sorry but I had a bit of a typo with the last command. This is the command to install:
```
sudo python setup.py install
```To install the program the setup file needs root privilege to install, thus the sudo command.

Hey, I made it! It's installed! Yupiii :) Thank you so much for all your help!

After installing, I restarted the computer and I thought it would automatically detect the wifi networks in range, but the Network tab shows "No wireless networks found".  The Refresh button has the same results. Are there any changes I should make in the Preferences?
I tried a wired connection and it works. it just doesn't seem to recognize wi-fi... 
And my Broadcom driver is not showing anymore in the Hardware drivers and in Network Settings I only have Wired Connection and Point to Point connection options but the Wireless Connection is not displayed anymore.

Do you have more suggestions?

Thank you,

---

### Post by Revolutionary101 on 2010-07-09
I'm am glad that you got the wired connection working.

However, I don't know how to get the wireless working.

I hope someone else can help you with that.

---

