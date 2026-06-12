---
title: "nvidia optimus and realtek"
date: 2012-02-08
forum: Multimedia Software
---

### Post by Angelikaklatte on 2012-02-08
Hi,
i have bought an Akoya Laptop with a Realtek digital home cinema soundcard and istalled as a convinced ubuntu user immediately the 11.10 32bit version. Unfortunatly neither the soundcard nor the   Nvidia Geforce 630m, nvidia Optimus can be recognised by the system. It is a real pity .. I have a basic grafic and sound function but it is only basic.
Until now I searched in different forums and on the Nvidia site but all I found out was that Nvidia Optimus is not working on Linux in the moment, they are working on it but for the moment nothing.
Can someone help?

thanks
angelika

---

### Post by wolfen69 on 2012-02-08
I make no guarantees, but the following might work:
```
sudo add-apt-repository ppa:https://launchpad.net/~bumblebee/+archive/stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install bumblebee bumblebee-nvidia
```
then
```
sudo usermod -a -G bumblebee $USER 
```
reboot.

---

### Post by Angelikaklatte on 2012-02-08
thanks for your fast help .... but ..... this is what I got
for the repository

"~$ sudo add-apt-repository ppa:[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 83, in get_ppa_info_from_lp
    return json.loads(lp_page)
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.7/json/decoder.py", line 384, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded


and for the apt-get
"E: cant find bumblebee 
E: cant find bumblebee-nvidia package"

---

