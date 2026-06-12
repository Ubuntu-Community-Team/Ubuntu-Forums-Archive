---
title: "Chromium with JAVA 1.6.0_16 plugin doesn't open my bank applet"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2009-10-05
Hi,
i posted my problem here:[http://ubuntuforums.org/showthread.php?t=1281935](http://ubuntuforums.org/showthread.php?t=1281935)

I installed Java, and tested it on javatester.org. Everything works fine, but my e-banking applet won´t open. I can login but then i have blank screen.

I run daily chromium:
4.0.221.5 Ubuntu build 27968


**about:plugins** shows for java:

```
Java(TM) Plug-in 1.6.0_16

Dateiname: libnpjp2.so
The next generation Java plug-in for Mozilla browsers.
MIME-Typ	Beschreibung	Suffixe	Aktiviert
application/x-java-vm	Java™ Plug-in		Ja
application/x-java-applet	Java™ Plug-in Applet		Ja
application/x-java-applet;version=1.1	Java™ Plug-in		Ja
application/x-java-applet;version=1.1.1	Java™ Plug-in		Ja
application/x-java-applet;version=1.1.2	Java™ Plug-in		Ja
application/x-java-applet;version=1.1.3	Java™ Plug-in		Ja
application/x-java-applet;version=1.2	Java™ Plug-in		Ja
application/x-java-applet;version=1.2.1	Java™ Plug-in		Ja
application/x-java-applet;version=1.2.2	Java™ Plug-in		Ja
application/x-java-applet;version=1.3	Java™ Plug-in		Ja
application/x-java-applet;version=1.3.1	Java™ Plug-in		Ja
application/x-java-applet;version=1.4	Java™ Plug-in		Ja
application/x-java-applet;version=1.4.1	Java™ Plug-in		Ja
application/x-java-applet;version=1.4.2	Java™ Plug-in		Ja
application/x-java-applet;version=1.5	Java™ Plug-in		Ja
application/x-java-applet;version=1.6	Java™ Plug-in		Ja
application/x-java-applet;jpi-version=1.6.0_16	Java™ Plug-in		Ja
application/x-java-bean	Java™ Plug-in JavaBeans		Ja
application/x-java-bean;version=1.1	Java™ Plug-in		Ja
application/x-java-bean;version=1.1.1	Java™ Plug-in		Ja
application/x-java-bean;version=1.1.2	Java™ Plug-in		Ja
application/x-java-bean;version=1.1.3	Java™ Plug-in		Ja
application/x-java-bean;version=1.2	Java™ Plug-in		Ja
application/x-java-bean;version=1.2.1	Java™ Plug-in		Ja
application/x-java-bean;version=1.2.2	Java™ Plug-in		Ja
application/x-java-bean;version=1.3	Java™ Plug-in		Ja
application/x-java-bean;version=1.3.1	Java™ Plug-in		Ja
application/x-java-bean;version=1.4	Java™ Plug-in		Ja
application/x-java-bean;version=1.4.1	Java™ Plug-in		Ja
application/x-java-bean;version=1.4.2	Java™ Plug-in		Ja
application/x-java-bean;version=1.5	Java™ Plug-in		Ja
application/x-java-bean;version=1.6	Java™ Plug-in		Ja
application/x-java-bean;jpi-version=1.6.0_16	Java™ Plug-in		Ja
application/x-java-vm-npruntime	Java™ Plug-in		Ja

```

Thanks for help

---

### Post by vickoxy on 2009-10-05
One picture:

P.S: i noticed that chromium can not load edit option on ubuntu forums. Is that only on my vomputer?

---

### Post by vickoxy on 2009-10-05
Bump!

Java shows properly that e-banking page in other browsers (tested in firefox 3/3.5, opera 10 and epiphany gecko/webkit), and i know that that page is running on all other older browsers...

Means, that only in chrome i occured on this issue...

---

### Post by steveneddy on 2009-10-05
Banking is a secure environment.

One could not expect a non-mainstream browser to be able to connect to a secure site like a banking site, would you?

Either use Firefox or a user agent switcher.

High security web sites will only allow certain browsers to access the contents of said web site.

---

### Post by vickoxy on 2009-10-05
I do not think that there is some bank policy about that-it says only: "you need java capable browser to use netbanking". 
And epiphany or opera are surely not so mainstream.

I think that there is some bug/issue only with chrome loading java applet on that site.

Other than that-this service is few years old, and i think it was mainly made for Windows users- but-as-said also other browser are loading just normal that site.

Thanks

---

### Post by vickoxy on 2009-10-05
> **steveneddy said:**
> Banking is a secure environment.

One could not expect a non-mainstream browser to be able to connect to a secure site like a banking site, would you?

Either use Firefox or a user agent switcher.

High security web sites will only allow certain browsers to access the contents of said web site.

And about user agent switcher-you think that chrome mask itself as firefox (there is that option in opera 10)? Is that possible? Because that would be awsome-only that page causing me major problems...

---

### Post by steveneddy on 2009-10-05
> **vickoxy said:**
> And about user agent switcher-you think that chrome mask itself as firefox (there is that option in opera 10)? Is that possible? Because that would be awsome-only that page causing me major problems...

Try it to see what happens.

Also try masking as Windows XP with IE!

---

### Post by vickoxy on 2009-10-06
> **steveneddy said:**
> Try it to see what happens.

Also try masking as Windows XP with IE!


Unfortunately, i do not know how to do that-in opera there was right mice click with that option.

So, if anybody can suggest how to...
Thanks

---

### Post by thecow on 2009-10-06
> **vickoxy said:**
> One picture:

P.S: i noticed that chromium can not load edit option on ubuntu forums. Is that only on my vomputer?

I am using chrome 4.0.220.1 and I can use the edit feature on this forum

Edit: Just did it ha

---

### Post by thecow on 2009-10-06
> **steveneddy said:**
> Banking is a secure environment.

One could not expect a non-mainstream browser to be able to connect to a secure site like a banking site, would you?

Either use Firefox or a user agent switcher.

High security web sites will only allow certain browsers to access the contents of said web site.
Ive never heard of this

---

### Post by vickoxy on 2009-10-06
> **thecow said:**
> I am using chrome 4.0.220.1 and I can use the edit feature on this forum

Edit: Just did it ha

Interesting, i am using 4.0.220.1 and i can not. also, on this forum i can not display picture attachments by clicking-need to open in new tab?!?

---

### Post by thecow on 2009-10-06
I can click on that picture and it opens like it is supposed to.  Im not sure why yours would act differently if we have the same software.  I will say that I am running Karmic beta but I cant imagine why that would change anything.  According to javatester I am running 1.6.0_15 .  Are you sure the edit feature is a java thing?  Maybe you are missing something else

---

### Post by vickoxy on 2009-10-06
> **thecow said:**
> I can click on that picture and it opens like it is supposed to.  Im not sure why yours would act differently if we have the same software.  I will say that I am running Karmic beta but I cant imagine why that would change anything.  According to javatester I am running 1.6.0_15 .  Are you sure the edit feature is a java thing?  Maybe you are missing something else

I couldn´t thing what else could it be. Bank applet not working, picture viewer and edit option at ubuntuforums.org and mydellmini.com (they use same engine-on other sites it is working normally).

Any idea?

P.S. i use Linux Mint 7 which is based on ubuntu 9.04...

---

### Post by vickoxy on 2009-10-07
If i open chromium in terminal, when i activate bank java applet, i get this message:

```
[25342:25342:9701253466:ERROR:/build/buildd/chromium-browser-4.0.221.7~svn20091006r28103/build-tree/src/webkit/glue/plugins/plugin_instance.cc(433)] Not implemented reached in NPError NPAPI::PluginInstance::GetServiceManager(void**)

```

Any idea?

---

### Post by vickoxy on 2009-10-08
STRANGE:
I installed google-chrome 4.0.221.8
and google-chromium 4.0.222.1 (Ubuntu build 28248)

And Chrome is loading ubuntuforums popup pictures and edit tab, but chromium not !?!

Still, bank applet behaviour is still the same...

Idea?

---

### Post by vickoxy on 2009-10-09
Well, and i think that my bank account problem is definitely chrome-bug-yesterday i installed on one mac leopard chrome and the behaviour with that page is just the same as with the linux version.

Other than that-i run chrome/chromium on dell mini 9 and is noticeably faster than other browsers. And it didn´t crash even once...

I use now only google-chrome. This is error popin out in terminal when i activate e-banking applet:
> [18106:18106:5989686400:ERROR:/usr/local/google/home/chrome-eng/b/slave/chrome-official-linux/build/src/webkit/glue/plugins/plugin_instance.cc(433)] Not implemented reached in NPError NPAPI::PluginInstance::GetServiceManager(void**)

Do i need here some webkit package?

---

