---
title: "i cant open the Contol Center or Synaptic"
date: 2009-06-02
forum: Mythbuntu
---

### Post by Senf on 2009-06-02
Hi guys my first big problem with Ubuntu i mean Mythbuntu.
i get it with : sudo apt-get install mythbuntu-desktop
i`am from Germany and the Konfguration in englisch has taken a long time! but it runs!
Then i will configure my Nivida with Synaptic packages i find NVTV for the TV-out and before i klick on a JAVA plugin crap packages.
He download and Install and give me this error message:

  	 	 	 	 	 	  E: Unable to write mmap - msync (28 No space left on device)  
 E: Die Paketlisten oder die Status-Datei konnte nicht geöffnet oder eingelesen werden.  
 E: _cache->open() failed, please report.


I have no idea where I get the report

Now i cant open the Contol Center or Synaptic
pleas help me thanks

[LEFT]if someone could explain me to German, I would be very grateful!!! now i use Google help to type this
[/LEFT]

---

### Post by LowSky on 2009-06-02
Sie müssen alte Akten löschen
geöffnet Terminal
lassen Sie diese Befehle laufen
```
sudo apt-get clean
sudo apt-get autoremove
```
Bringen Sie jetzt andere Pakete an. Hoffnungsvoll arbeiten sie


Ich spreche nicht deutsch, ich verwendete [Yahoo Bablefish]("http://babelfish.yahoo.com/translate_txt") zu übersetzen



Ich hoffe, dass Sie meine Anweisungen verstehen

In English

Go to Terminal
run these commands
```
sudo apt-get clean
sudo apt-get autoremove
```

then try to instal the other packages. I hope this helps

---

### Post by Senf on 2009-06-04
Thanks a lot!!! System run now

---

