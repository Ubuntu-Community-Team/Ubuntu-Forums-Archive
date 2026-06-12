---
title: "Firefox certificate importing not working through command line Ubuntu16 and 18"
date: 2018-10-17
forum: Multimedia Software
---

### Post by dwalker-8 on 2018-10-17
I followed the steps in this link [https://wiki.mozilla.org/CA:AddRootToFirefox](https://wiki.mozilla.org/CA:AddRootToFirefox) to add root certificates to firefox without going through the preferences window.  It's under the section header Autoconfig Via Javascript.  Basically, you put the autoconfig.js file inside /usr/lib/firefox/defaults/pref directory and put the mozilla.cfg file inside /usr/lib/firefox directory where the mozilla.cfg file contains a line 
cert =
where the contents of your root certificate go after the = sign with no line breaks.  This method works on all other linux distros my team is testing out including rhel6 + 7, centos 6 + 7, opensuse, fedora, debian 9 etc. except Ubuntu 16 and 18. To test this we put those two files where they need to go according to mozilla, close the firefox browser so that any changes get re-read from the config files, and navigate to our internal https url and it still continues to give us a security exception error in the browser.  Does anyone know if Ubuntu does this a different way than other distros?  Also, this needs to be done in the command line.  This actually works if you do it by hand through firefox preferences window and point it to your certificate but that is not going to work for my team's purpose.

Thanks!

---

