---
title: "skype for bitlbee won't connect to server"
date: 2008-12-17
forum: Multimedia Software
---

### Post by Poyntz on 2008-12-17
for some reason I can't get skype for bitlbee to connect.
what I've done:
1. i edited the extracted bitlbee-skype-0.6.3 directory/skyped.py file and changed: self.skype = Skype4Py.Skype()
to:      self.skype = Skype4Py.Skype(Transport='dbus')
2. i've built bitlbee-skype-0.6.3 and Skype4Py-1.0.31.0 from source
3. i created skyped.cert.pem and skyped.key.pem in /usr/local/etc/skyped
(ie, [I]openssl req -new -x509 -days 365 -nodes -config skyped.cnf -out skyped.cert.pem \
        -keyout skyped.key.pem[/I] )
3. i edited /usr/etc/skyped/skyped.conf to contain my username, the md5 hash of my password and the locations of skyped.cert.pem and skyped.key.pem
4. i loaded **bitlbee** in shell
5. i loaded **skyped** in shell
*(**ps ax | grep skyped** doesn't return anything for some odd reason...)*
6. i loaded up irssi and connected to localhost
7. i type identify <pass>
8. i type add account skype <user> <md5 pass hash>
or,
8. i type add account skype <user> <pass>
9. i type **account on**

I get the message:
<@root> skype - Logging in: Connecting
<@root> skype - Couldn't log in: Could not connect to server
<@root> skype - Logging in: Signing off..

I have several accounts added: MSN, Yahoo and ICQ and all of them work apart from skype.

Is there a way to get this plugin working in ubuntu? am I doing something wrong?

I like the low resource intensiveness of irssi as opposed to pidgin and would like to transfer from application to application completely if at all possible. Whilst I could theorhetically have skype and irssi open, it would be better if I could do skype chat through irssi.

---

