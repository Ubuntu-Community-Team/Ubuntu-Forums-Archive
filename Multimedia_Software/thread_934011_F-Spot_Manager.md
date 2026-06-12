---
title: "F-Spot Manager"
date: 2008-09-30
forum: Multimedia Software
---

### Post by zkab on 2008-09-30
How can I rename an image in F-Spot Manager :confused:

---

### Post by arkticcool on 2008-09-30
I have no idea, because there are better alternatives out there. Google's picasa is the one I use I recommend that you install that, and use it.

Launch terminal from **(Applications -> Accessories -> Terminal)** and issue the following command in the terminal window:
```
wget http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.7.3736-15_i386.deb
```

once complete enter the following command:
```
sudo dpkg -i picasa_2.7.3736-15_i386.deb
```

After completing above step you can launch Google picasa from **(Applications -> Other -> Picasa )**

---

### Post by zkab on 2008-09-30
Thanks for your answer.
I have heard that Picasa needs Wine to run ... if so it is not a native Linux apps :confused:

---

### Post by arkticcool on 2008-09-30
Not at all. If you execute the above commands it will download and install the .deb package of Picasa, made for debain systems like ubuntu. Heres a site that can guide you through the installation:[http://www.ubuntugeek.com/install-google-picasa-image-organizer-in-ubuntu.html]("http://www.ubuntugeek.com/install-google-picasa-image-organizer-in-ubuntu.html")

---

### Post by zkab on 2008-10-01
Maybe I got it all wrong but checking FAQ in picasa.google.com/linux/faq.html there is a lot of talk about Wine ...
------------------------------------------------------------------------
Q: Is Picasa for Linux open source?

Picasa for Linux isn’t open source; it uses a carefully tested version of Wine to run the current Windows version of Picasa. Wine itself is an open-source implementation of the Windows API. It runs on top of the X Window System and Linux or Unix.
------------------------------------------------------------------------
I still have a feeling that Picasa is not a native Linux apps ... correct me if I am wrong

---

### Post by ReddogOne on 2008-10-01
> **zkab said:**
> Maybe I got it all wrong but checking FAQ in picasa.google.com/linux/faq.html there is a lot of talk about Wine ...

AFAIK it uses WINE but you don't have to worry about setting it up. It wraps the application with bit of WINE so you don't have to!

---

### Post by zkab on 2008-10-01
OK - I tested Picasa 3 beta and found that a portion of Wine was installed.
What I don't understand is why Google has not developed a pure Linux version of Picasa instead of keeping some of the software still Windows based and therefore rely on Wine ... Google is afterall a Microsoft competitor and should get away from developing software that belongs to Windows environment ... :)

---

### Post by arkticcool on 2008-10-01
They've done the same with their new browser, Chrome. It's because the large majority of internet users still use Windows, and they trade off a Linux edition, to spend more time creating a better/faster windows edition. Majority rules in big business.

Smart business decision, not as good for us though.

But now I'm getting off topic. I get the feeling that you've solved your problem.

---

### Post by zkab on 2008-10-02
Thanks guys :D

---

