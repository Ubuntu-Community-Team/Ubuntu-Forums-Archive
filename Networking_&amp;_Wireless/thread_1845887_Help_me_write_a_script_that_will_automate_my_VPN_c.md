---
title: "Help me write a script that will automate my VPN connection"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by seshomaru samma on 2011-09-17
I would like to have a script on my desktop ,clicking on it will connect me to a VPN server. At the moment I need to open a terminal
cd to /etc/openvpn and then run this command:sudo openvpn --config 15\ -\ ibVPN\ USW.ovpn 
I then need to input my sudo password and my VPN credentials. I don't mind doing it, but my wife thinks it's 'complicated'. For some reason Network Manger can't connect to the VPN , only command line works, so a script is needed
Any help would be appreciated

---

### Post by seshomaru samma on 2011-09-20
this is what i've got so far :
```
#!/bin/bash
cd /etc/openvpn
sudo openvpn --config 12\ -\ itVPN\ USW.ovpn --auth-user-pass credentials 
```
When I run it I can see it going through the authentication process in the terminal but then the terminal just shuts off. I know it didn't connect cause I can't find an openvpn process running.
I'm also not sure how my credentials file should look like- I tried like this:
```
Xauth username ${myusername}
Xauth password ${mypassword}
```
as well as :
```
myusername
mypassword
```
With the same results. Am I correct that I should locate the credentials file in /etc/openvpn?

---

### Post by josephmills on 2011-09-20
you are using gnome/unity or kde ?

---

### Post by josephmills on 2011-09-20
```


#!/bin/bash 


gnome-terminal --working-directory /etc/openvpn -e 'bash -lc "cd /etc/openvpn ;sudo openvpn --config 12\ -\ itVPN\ USW.ovpn --auth-user-pass credentials ;bash"'


```



that should work for gnome

---

### Post by josephmills on 2011-09-20
Well did it work ????

---

### Post by seshomaru samma on 2011-09-21
> Well did it work ????
Sorry for the late reply,
I've modified the script according to your suggestion and indeed the terminal does not quit.It is trying to connect, but now I'm getting this:
```

 AUTH: Received AUTH_FAILED control message

```
which shows me that the authentication is not working. I can see several options:
1. the credentials file is in the wrong format
2. the credentials file is in the wrong directory (it's now in etc/openvpn)
3. something else
 
 in the man page for openvpn it says :
> Note: OpenVPN will only read  passwords  from  a  file  if  it  has  been built with the --enable-password-save configure option
not sure where to go from here....

---

### Post by seshomaru samma on 2011-09-29
got it,
just needed to specify the location of the credentials file, that's all
so final script:
```
#!/bin/bash 


gnome-terminal --working-directory /etc/openvpn -e 'bash -lc "cd /etc/openvpn ;sudo openvpn --config 12\ -\ itVPN\ USW.ovpn --auth-user-pass /etc/openvpn/credentials ;bash"'
```

---

