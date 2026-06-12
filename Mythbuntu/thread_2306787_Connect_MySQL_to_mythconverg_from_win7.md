---
title: "Connect MySQL to mythconverg from win7"
date: 2015-12-18
forum: Mythbuntu
---

### Post by gga96 on 2015-12-18
I have have had mythtv running now for about 2 years and now I would like  to connect MySQL to mythconverg from a win7 machine on the LAN.
  
 I understand to do this I am required to use an SSH tunnel. I have tried to  make sense of the documentation but I am getting more and more confused.
  
 Can you please help me to get the SSH created and configured correctly  on mythbuntu (14.04) so the connection to mythconverg from win7  works. 
  
 All help appreciated.
  
 Regards
 Glen

---

### Post by blm-ubunet on 2015-12-18
Do you want to run a FE on the windows box ?

If your existing mythtv setup a combined BE/FE ?
And using 127.0.0.1 loop localhost IP address?

Installations using localhost are a pain to fix.

Mythconverg is the name of mythtv database schema hosted by mysql server normally running on MBE.
You connect with a mysql client to the MBE mysql server.

---

### Post by gga96 on 2015-12-19
Thanks for you reply.

I have a LAN with a FE in the lounge,  BE/FE and my main Win development machine in the study. I do not want to change this myth arrangement.

What I want to do is connect using MySQL with the myth database mythconverg from the Win7 machine. 

I have had trouble creating and configuring the required SSH protocol.

Glen

---

### Post by steeldriver on 2015-12-19
What mysql client are you using on the Windows machine? Does it have a built-in tunneling capability or are you using an external SSH program (PuTTY?)?

If you are doing all this over your own LAN then (provided your router settings are sane) do you really need to tunnel the connection over SSH?

---

### Post by gga96 on 2015-12-19
Thank you both for your help.

I have discovered the error of my ways. I had miss read the documentation and thought that SSH was required when in fact it is only necessary for admin function like open and close the server etc.

Clearly SSH is not require.

Thanks again

Glen

---

