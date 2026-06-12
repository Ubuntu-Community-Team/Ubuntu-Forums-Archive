---
title: "How to install Signal Messenger on Lubuntu"
date: 2020-08-16
forum: Multimedia Software
---

### Post by somamint on 2020-08-16
Hello,

i just switched to Lubuntu on my old netbook. So far everything works. But i can't install Signal.
I tried it from the website. NO success. Then i tried it like on ubuntu 18.04 which is my lubuntu based on. No success
There no finding the package.

Any Solution would be appreciate :)

---

### Post by overdrank on 2020-08-16
Hi and welcome, a little more info would help us help you. What is signal, is it in the repos?

---

### Post by CatKiller on 2020-08-16
Your first choice shouldn't be downloading things from websites.

Signal is available as a snap. You can install it with ```
sudo snap install signal-desktop
```

---

### Post by somamint on 2020-08-16
Hello :)

i tried "> sudo snap install signal-desktop". But this version don't want to start. 

Not sure what i meant  with respos but the programm i'm takling about is "[https://www.signal.org](https://www.signal.org)/"

I tried the command from the website:
> 
curl -s [https://updates.signal.org/desktop/apt/keys.asc](https://updates.signal.org/desktop/apt/keys.asc) | sudo apt-key add -
echo "deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main" | sudo tee -a /etc/apt/sources.list.d/signal-xenial.list
sudo apt update && sudo apt install signal-desktop

But its telling me he is not finding any signal-desktop

I tried 

> sudo apt install signal-desktop

And got the error 

> "E: Packet signal-desktop cannot be found."
What kind of information would be helpful?

---

### Post by deadflowr on 2020-08-16
> What kind of information would be helpful?
The output of sudo apt update.

Also, if the snap is still installed please run
```
snap run signal-desktop
```
and post the output it generates.

---

### Post by somamint on 2020-08-16
Oh i forgot.

If i try to use "sudo snap install signal-desktop"

i get 

> error: snap "signal-desktop" is not available on stable but is available to
       install on the following channels:

       edge       snap install --edge signal-desktop

       Please be mindful pre-release channels may include features not
       completely tested or implemented. Get more information with 'snap info
       signal-desktop'.

so i install signal with

" snap install --edge signal-desktop"

after install i tried 

> /snap/signal-desktop/292/snap/command-chain/desktop-launch: line 543: /snap/signal-desktop/292/opt/Signal/signal-desktop: cannot execute binary file: Exec format error
/snap/signal-desktop/292/snap/command-chain/desktop-launch: line 543: /snap/signal-desktop/292/opt/Signal/signal-desktop: Success

Output of sudo apt update:

```
sudo apt update
[sudo] password for ...
Holen:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]
OK:2 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu bionic InRelease      
OK:3 http://de.archive.ubuntu.com/ubuntu bionic InRelease                      
OK:4 http://de.archive.ubuntu.com/ubuntu bionic-updates InRelease              
OK:5 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic InRelease          
OK:6 http://de.archive.ubuntu.com/ubuntu bionic-backports InRelease            
OK:7 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                 
OK:8 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic InRelease  
Ign:9 https://updates.signal.org/desktop/apt bionic InRelease                
OK:10 https://updates.signal.org/desktop/apt xenial InRelease
Fehl:11 https://updates.signal.org/desktop/apt bionic Release
  404  Not Found [IP: 2600:9000:20c3:dc00:16:675e:2280:93a1 443]
Paketlisten werden gelesen... Fertig
E: Das Depot »https://updates.signal.org/desktop/apt bionic Release« enthält keine Release-Datei.
N: Eine Aktualisierung von solch einem Depot kann nicht auf eine sichere Art durchgeführt werden, daher ist es standardmäßig deaktiviert.
N: Weitere Details zur Erzeugung von Paketdepots sowie zu deren Benutzerkonfiguration finden Sie in der Handbuchseite apt-secure(8).
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-bionic.list:1 und /etc/apt/sources.list.d/signal-bionic.list:2
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:5
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:6
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:7
W: Ziel Packages (main/binary-amd64/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Packages (main/binary-all/Packages) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Translations (main/i18n/Translation-de_DE) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Translations (main/i18n/Translation-de) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel Translations (main/i18n/Translation-en) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11 (main/dep11/Components-i386.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11 (main/dep11/Components-all.yml) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11-icons-small (main/dep11/icons-48x48.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel DEP-11-icons (main/dep11/icons-64x64.tar) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel CNF (main/cnf/Commands-i386) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8
W: Ziel CNF (main/cnf/Commands-all) ist mehrfach konfiguriert in /etc/apt/sources.list.d/signal-xenial.list:4 und /etc/apt/sources.list.d/signal-xenial.list:8



```

---

### Post by deadflowr on 2020-08-16
First things first clean up the source.list files.
Post back
```
cat /etc/apt/sources.list.d/signal-xenial.list 
cat /etc/apt/sources.list.d/signal-bionic.list
```
To see what you're dealing with there.


Second, something's wrong with the snap output.
The revision is too old to have just downloaded.
current revision is 327, not 292.
I went and did a quick install, and it never warned me about any edge version,
What does
```
snap info signal-desktop
```
show?

Also , for what it's worth (and this really doesn't solve the other issues at all, but...), there is also a flatpak version,
see [https://flathub.org/apps/details/org.signal.Signal]("https://flathub.org/apps/details/org.signal.Signal")

---

### Post by somamint on 2020-08-16
output:
> 
cat /etc/apt/sources.list.d/signal-xenial.list 
# deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
# deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
# deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main

cat /etc/apt/sources.list.d/signal-bionic.list
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) bionic main
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) bionic main

and 

> snap info signal-desktop
name:      signal-desktop
summary:   Signal Private Messenger for Windows, Mac, and Linux
publisher: Snapcrafters
store-url: [https://snapcraft.io/signal-desktop](https://snapcraft.io/signal-desktop)
contact:   [https://github.com/snapcrafters/signal-desktop/issues](https://github.com/snapcrafters/signal-desktop/issues)
license:   unset
description: |
  Say anything
  
   - Send high-quality group, text, voice, video, document, and picture
   messages anywhere in the world without SMS or MMS fees.
  
  Speak freely
  
  - Make crystal-clear voice and video calls to people who live across town,
  or across the ocean, with no long-distance charges.
  
  Stay private
  
  - Signal messages and calls are always end-to-end encrypted and
  painstakingly engineered to keep your communication safe. We can't read
  your messages or see your calls, and no one else can either.
  
  Control time
  
   -  Keep your chat history tidy with messages that you can set to
   disappear. Choose different disappearing message intervals for each
   conversation. Everyone in the thread shares the same setting. Good
   memories will last even if the words vanish.
  
  Free for everyone
  
   - Signal is made for you. As an Open Source project supported by grants
   and donations, Signal can put users first. There are no ads, no affiliate
   marketers, no creepy tracking. Just open technology for a fast, simple,
   and secure messaging experience. The way it should be.
  
  This snap is maintained by the Snapcrafters community, and is not
  necessarily endorsed or officially maintained by the upstream developers.
commands:
  - signal-desktop
snap-id:      r4LxMVp7zWramXsJQAKdamxy6TAWlaDD
tracking:     latest/edge
refresh-date: today at 18:31 CEST
channels:
  latest/stable:    –                             
  latest/candidate: –                             
  latest/beta:      –                             
  latest/edge:      1.30.0 2020-01-24 (292) 132MB -
installed:          1.30.0            (292) 132MB -

i tried flatpack as well and don't want to find any package either.

---

### Post by deadflowr on 2020-08-16
Hmm, I have a quick guess,
What does 
```
uname -a
```
show?

---

### Post by somamint on 2020-08-16
:)

> uname -a
Linux Somavakien 4.15.0-112-generic #113-Ubuntu SMP Thu Jul 9 23:41:06 UTC 2020 i686 athlon i686 GNU/Linux

---

### Post by deadflowr on 2020-08-16
Yep.
Sorry.
i686 means 32-bit.

Signal is 64-bit only.
[https://github.com/signalapp/Signal-Desktop/issues/1661]("https://github.com/signalapp/Signal-Desktop/issues/1661")

You can remove(delete) the sources.list files
```
sudo rm /etc/apt/sources.list.d/signal-xenial.list 
sudo rm /etc/apt/sources.list.d/signal-bionic.list 
```
That will at least clean up the apt output.

---

### Post by somamint on 2020-08-16
ahhh ****, so  i need to download 64 bit :D, ok i will try it and then i will be pack to answer :)

---

### Post by somamint on 2020-08-16
So installed 64 Bit Lubuntu and Snap Install from Signal works out of the box!!

Thanks so much :)

---

