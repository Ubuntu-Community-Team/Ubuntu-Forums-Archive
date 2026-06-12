---
title: "Openvpn how to setup correctly in Ubuntu 12.04/12.10/13.04"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by mirearts KING SUNNY on 2013-08-10
[B]Hello after some hard fighting, I have finally how to create a VPN connection and bypass the famous GREY 'save' button.

[/B]What you need isa** CERTIFICATE **from the VPN service you want to create (if using network-manager GUI) copy and paste the .crt file in /etc/openvpn/. If you did not get the .crt file then create one by opening the .ovpn configuration file you downloaded and open with gedit and select section starting from '<cer> till end of cert' and paste in the new text document and save it as .crt and move it to the /etc/openvpn folder (use sudo nautilus /home)

1. Download and extract server configuration files for Openvpn.

[ATTACH=CONFIG]245251[/ATTACH]

2. Open one of the configuration file to copy the certificate details. 

[ATTACH=CONFIG]245252[/ATTACH]

3. Copy the above and paste in a new blank document and save as myvpnconnection.crt in desktop or home.

4. Open Terminal and paste : sudo nautilus /etc/openvpn, and paste the .crt document you just created. 

5. As usual proceed to import wizard and select 'PASSWORD' from the authentication typee. In the 'Certificate' box select the file you just paste in /etc/openvpn. 

6. Input your username and password, and save!

[ATTACH=CONFIG]245253[/ATTACH]

[ATTACH=CONFIG]245254[/ATTACH]

If that does not work for you, you can use terminal to setup your Openvpn connection.

simply browse to your folder where you extracted the files, and making sure you have openvpn installed, proceed as follows:

cd /home/myvpnconnectionfileslocation
ls (this will display all files in that location)
sudo openvpn --config myopenvpnsetupfile.ovpn
finished that's all.

PS: with the above method you will not be notified graphically if u r connecte to a VPN server unless you go and check your IP adress and location.

---

