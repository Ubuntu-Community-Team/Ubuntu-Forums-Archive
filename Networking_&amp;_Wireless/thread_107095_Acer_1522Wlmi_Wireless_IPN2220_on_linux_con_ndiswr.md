---
title: "Acer 1522Wlmi Wireless IPN2220 on linux con ndiswrapper"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by freewalker1 on 2005-12-22
Acer 1522Wlmi Wireless IPN2220 on linux con diswrapper
Visto che ci ho messo un po' per riuscire a far funzionare la wireless del mio acer 1522Wlmi su ubuntu a 64bit e hovisto che molti altri avevano problemi posto come fare:

1)Scaricate ndiswrapper --> Attualmente l'ultima versione è la 1.7 scaricabile da:
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)
2)Scaricate i driver della scheda wireless per 64 bit da :
[http://www.planetamd64.com/index.php...&st=0&p=62758&](http://www.planetamd64.com/index.php...&st=0&p=62758&)
3)installate ndsiwrapper, basta seguire la guida che trovate su
[http://ndiswrapper.sourceforge.net/m...ll_NDISWrapper](http://ndiswrapper.sourceforge.net/m...ll_NDISWrapper)
4)estraete i driver in una cartella per esempio /wdriver
5)rinominate il file neti2220X64.inf in i2220nta.inf (li trovate in /wdriver), questo passaggio è importate!!
6)ora potete installare il dirver :
#ndiswrapper -i /wdriver/i2220nta.inf
7)controllate se è installato correttamente con :
#ndiswrapper -l
che deve rispondere :
Installed drivers:
i2220nta driver present, hardware present
8)installate il modulo di ndsiwrapper
#modprobe ndiswrapper
9)controllate che funzioni con
#lsmod
dovreste avere un elenco in cui c'è pure ndiswrapper
10)ora riavviate il servizio di networking con il comando :
#/etc/init.d/networking restart
11)dovrebbe andare potete usare iwconfig ed ipconfig per impostare la vostra connessione che dovrebbe risultare com wlan0

ps vi conviene fare tutto loggati da root cosi' nn avete problemi di autorizzazioni

Saluti

---

