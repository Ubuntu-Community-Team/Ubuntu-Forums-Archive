---
title: "AccessRunner ADSL WAN Adapter (PCI) via PPPoE and Ubuntu"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by benskiedra on 2006-03-02
Hello everybody,

I've just installed my new fresh copy of Ubuntu so as you now know I'm "green" to linux. I've decided to connect to the internet but it seems it's not as easy as I thought. I have a PCI (internal) ADSL modem (AccessRunner ADSL WAN adapter) and I'm not able to make a connection (PPPoE) with it... I've tried running scripts from rp-pppoe but it gave me nothing. I've also tried running the default Ubuntu configuration (pppoeconfig) but it didn't find my modem when I pressed the AUTODETECT button... I wonder - maybe it's because there's no drivers for the modem? Checked this out too but I don't understand anything... It says that I need to install something like kernel headers huh and some ATM thing... Don't understand these things correctly... Maybe someone could help me? Thanks in advance.

Ben,
Lt.

---

### Post by benskiedra on 2006-03-03
Hello again,

I found out a direct name of my modem... It's PLANET ADP-8301. The problem is that there are no official drivers for it to work on Linux. I know there's some way to make it "visible" to linux through /dev/modem/ port but without any help I can't find it...

ANy Help? :neutral:

---

### Post by mips on 2006-03-03
[http://www.google.co.za/search?q=+linux+AccessRunner+ADSL&hl=en&hs=XeB&lr=lang_en&client=firefox-a&rls=org.mozilla:en-GB:official_s&as_qdr=all&start=10&sa=N](http://www.google.co.za/search?q=+linux+AccessRunner+ADSL&hl=en&hs=XeB&lr=lang_en&client=firefox-a&rls=org.mozilla:en-GB:official_s&as_qdr=all&start=10&sa=N)

[http://ubuntuforums.org/showthread.php?p=5629](http://ubuntuforums.org/showthread.php?p=5629)
[http://ubuntuforums.org/showthread.php?t=1906](http://ubuntuforums.org/showthread.php?t=1906)
[http://gentoo-wiki.com/HOWTO_PPPoA_ADSL_with_a_Conexant_Accessrunner_PCI_modem](http://gentoo-wiki.com/HOWTO_PPPoA_ADSL_with_a_Conexant_Accessrunner_PCI_modem)
[http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html](http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html)
[http://www.unixhead.org/docs/conexant/linux-conexant-howto.html](http://www.unixhead.org/docs/conexant/linux-conexant-howto.html)    ### Look at the Debian related stuff.
[http://www.chipweb.de/dsl/index.php?menu=2&level=10](http://www.chipweb.de/dsl/index.php?menu=2&level=10)
[http://accessrunner.sourceforge.net/index.shtml](http://accessrunner.sourceforge.net/index.shtml)

---

