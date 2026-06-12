---
title: "No Root priv error"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by mikecanada on 2009-01-10
Morning All,

I am using Ubuntu 8.10 with a hardware modem set with gnome ppp the modem was found and dials out perfect then 2 seconds later drops the line.The log says

Starting pppd at Friday Jan...
PID of pppd 5497
Disconnecting at Friday Jan...
The PPP daemaon has died: No root priv error {exit code =3}
I guess that,s it for now exiting.

I googled the problem and didn,t find a solution,sounds like as a user I don,t own the ppp daemon.Has anybody a answer ? Thanks Mike

---

### Post by mikecanada on 2009-01-11
Well I guess we can mark this as resolved as I found the same problem some one had a while back,the only solution so far as I see is open terminal:
sudo gnome- ppp
then fill in dial up box
then the system connects fine

Seems like the Ubuntu people have abandon the modem users,the modem is not even a option in the Network Manger.I thought this odd as so many rural people have no other option than the modem.Thanks for looking Mike

---

### Post by Luciano-UB on 2009-01-11
> **mikecanada said:**
> Well I guess we can mark this as resolved as I found the same problem some one had a while back,the only solution so far as I see is open terminal:
sudo gnome- ppp
then fill in dial up box
then the system connects fine

Seems like the Ubuntu people have abandon the modem users,the modem is not even a option in the Network Manger.I thought this odd as so many rural people have no other option than the modem.Thanks for looking Mike
Resolve this with:

chmod +s /usr/sbin/pppd

anyway, for other problems try this:

chmod 777 /usr/sbin/pppd
chmod 777 /etc/ppp/chap-secrets
chmod 777 /etc/ppp/pap-secrets
chmod 777 /etc/ppp/peers/
chmod 777 /etc/ppp/peers/wvdial
chmod 777 /etc/ppp/peers/wvdial-pipe

good luck! bye.

---

### Post by mikecanada on 2009-01-11
Many Thanks for taking the time to help a complete stranger,I will try that.
                  Cheers Mike

---

