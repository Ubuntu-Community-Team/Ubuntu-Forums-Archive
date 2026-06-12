---
title: "Pidgin gets certificate error trying to login to MSN."
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by jeremyazevedo@gmail.com on 2010-11-18
This morning I had trouble logging into MSN via Pidgin. I kept getting the error “The certificate for omega.contacts.msn.com could not be validated. The certificate chain presented is invalid."
 
Seems the folks in Redmond decided to change something overnight, and a few minutes searching turned up this post, which resolved the issue for me. Just wanted to pass it on here for future reference.
 
[http://retrohack.com/why-cant-we-all-just-get-along/#more-3107](http://retrohack.com/why-cant-we-all-just-get-along/#more-3107)
 
The link references Windoz 7, so the path I used on 10.10 is 
/home/username/.purple/certificates/x509/tls_peers
 
Hope this helps someone out!

---

### Post by vercellone on 2010-11-18
Works as advertised.  Much appreciated!

---

### Post by curVV on 2010-11-18
Thanks! =D>

---

### Post by naqiboy on 2010-11-18
Hello
I went to the link [https://omega.contacts.msn.com/](https://omega.contacts.msn.com/) but i get :

Directory Listing Denied
This Virtual Directory does not allow contents to be listed.


any ideas??

---

### Post by mnichau on 2010-11-18
> **naqiboy said:**
> Hello
I went to the link [https://omega.contacts.msn.com/](https://omega.contacts.msn.com/) but i get :

Directory Listing Denied
This Virtual Directory does not allow contents to be listed.


any ideas??

See step 2 at:

[http://retrohack.com/why-cant-we-all-just-get-along/#more-3107](http://retrohack.com/why-cant-we-all-just-get-along/#more-3107)

---

### Post by kismeras on 2010-11-18
> **jeremyazevedo@gmail.com said:**
> This morning I had trouble logging into MSN via Pidgin. I kept getting the error “The certificate for omega.contacts.msn.com could not be validated. The certificate chain presented is invalid."
 
Seems the folks in Redmond decided to change something overnight, and a few minutes searching turned up this post, which resolved the issue for me. Just wanted to pass it on here for future reference.
 
[http://retrohack.com/why-cant-we-all-just-get-along/#more-3107](http://retrohack.com/why-cant-we-all-just-get-along/#more-3107)
 
The link references Windoz 7, so the path I used on 10.10 is 
/home/username/.purple/certificates/x509/tls_peers
 
Hope this helps someone out!

Rock on...thanks :popcorn:

---

### Post by StarLab on 2010-11-18
I *was* having this problem. However, before I could apply the above solution, it worked itself out somehow. <shrug>

---

### Post by kgr132 on 2010-11-18
This solution worked exactly as advertised. 60 seconds later, Pidgin is logged in to MSN. Thanks a bunch.

---

### Post by opm595 on 2010-11-18
Champion stuff! 
Thanks heaps, fixed the problem right away.
Legend Mate!

---

### Post by wolterh on 2010-11-18
This doesn't work for me :S The error persists

[EDIT] After a while it started working, I can't tell how much because I went for a meal and when I came back and retried to connect it worked.

---

### Post by arubislander on 2010-11-19
Many thanks, works in Windows also.

---

### Post by mizar001 on 2010-11-19
No way. Every method i tried solved temporarily the problem.

Everytime i restart pidgin the error is showing up, and it fill my desktop with alert windows over time. 
It is completely unusable.

I deleted physical files of certificates in .pulse/... , disabled/enabled account, changed connection method, used tools->certificate window to delete certs, but nothing worked definitively.

This forced me to shutdown pidgin.

NOOOOOOO..... i found .... it's NOT pulse dir, it's purple dir !!!!! :D sorry. I deleted all pulse setting, unable to saw how stupid i am...

---

### Post by anonymousrobot on 2010-11-19
I can't even view the certificate for [http://omega.contacts.msn.com/](http://omega.contacts.msn.com/)

---

### Post by anonymousrobot on 2010-11-19
Here's a screenshot. There's no view certificate button here.

[IMG]http://i.imgur.com/gtZhB.png[/IMG]

---

### Post by arubislander on 2010-11-19
You should use http**s**, not http. And click on the padlock, not page info...

---

### Post by chili555 on 2010-11-19
Worked perfectly for me. Thank you.

---

### Post by anonymousrobot on 2010-11-19
> **arubislander said:**
> You should use http**s**, not http. And click on the padlock, not page info...

Thanks bro it worked.

---

### Post by wolterh on 2010-11-19
Hmm, sorry to keep this confusion going but it keeps not working. As mizar said, everything works temporarily.
When I visit the certificate page, even through https protocol, I get a SSL Error. Replacing the old certificate is no permanent fix - at least here at my end.

---

### Post by WSDsmurf on 2010-11-19
Thank you!

---

### Post by Jackie999 on 2010-11-20
> **woli said:**
> Hmm, sorry to keep this confusion going but it keeps not working. As mizar said, everything works temporarily.
When I visit the certificate page, even through https protocol, I get a SSL Error. Replacing the old certificate is no permanent fix - at least here at my end.


Agreed - same thing here, every time I reboot the error comes back.

---

### Post by opm595 on 2010-11-20
Mine worked Ok for the last few days, however it's now just drop-out again. 
They're more then likely moving office furniture around at Redmond, and someone's tripped on the cable again, causing it to unplug :) - Wish I could can my MSN account althogether, that'd even be a better solution.

It'll work itself out. After all we're Linux users, it always does!

---

### Post by misosofos on 2010-11-23
It doesn't work for me either. Any real solution? I can't get the certificate. Even with "https:" instead "http:".

---

### Post by molo on 2010-11-24
Apparently, Pidgin 2.7.7 fixes the issue, but it looks like it hasn't been packaged for Ubuntu yet (I'm using 10.04).   It's available for Fedora on the Pidgin website, however.

Hopefully the Ubuntu version is released soon, since compiling from source is a hassle...

---

### Post by Nagarajshet on 2010-11-25
HI .
I am able to connect to MSN server using MSN8 protocol  in java and retrieve contacts also.
But when the server send challenge string CHL 0 1991989189818929829929.
i am sending reply as 

[ 
left] MessageDigest mdEnc = MessageDigest
.getInstance("MD5");
int startIndex = reply.indexOf("0") + 2;

String toEnc = reply.substring(startIndex); // Value
toEnc.concat("Q1P7W2E4J9R8U3S5"); // to;
// encrypt

mdEnc.update(toEnc.getBytes(), 0, toEnc
.length());
String md5 = new BigInteger(1, mdEnc.digest())
.toString(16); // Encrypted string
out.println("QRY 9 [email]msmsgs@msnmsgr.com[/email] 32\r\n "
+ md5);
[/left]


but server is returning null.

I have verified my MD5 encryption is proper.
Please help me..

---

### Post by Jackie999 on 2010-11-30
Any suggestions on another simple messenger application? Pidgin is giving me these certificate errors on and off all day long on both ubuntu and Vista - I need to find something that works.

---

### Post by slumbergod on 2010-11-30
Pidgin gave me some certificate message then disconnected itself and won't connect again. Tried mucking around with certificates, purging and reinstalling pidgin, deleting .purple and restarting pidgin again, and even tried connecting in aMSN.

Looks like I will have to be patient until their certificate server is working properly.

---

### Post by kismeras on 2010-12-01
> **slumbergod said:**
> Pidgin gave me some certificate message then disconnected itself and won't connect again. Tried mucking around with certificates, purging and reinstalling pidgin, deleting .purple and restarting pidgin again, and even tried connecting in aMSN.

Looks like I will have to be patient until their certificate server is working properly.

I updated to the latest version of pidgin and all is well.

---

