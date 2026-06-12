---
title: "OpenVpn For Confused New Users; 12.04 LTS"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by 23aka23 on 2013-07-17
[FONT=Candara][SIZE=3]After weeks of struggling through every guide [/SIZE][/FONT][FONT=Candara][SIZE=3][FONT=Candara][SIZE=3] to setting-up and accessing a vpn connection[/SIZE][/FONT] that I could find on this board, the web, and by my own machinations, I was hand-held over the course of five days through a process that works first time, every time [/SIZE][/FONT][FONT=Candara][SIZE=3][FONT=Candara][SIZE=3] (I tried it more than once)[/SIZE][/FONT] by the tech department at PrivateInternetAccess, a commercial provider of vpn servers. I don't work for them. I pay them for access to their vpn. I can't say enough in a positive way about PIA. I highly recommend their service and support, but the instructions below will work in setting up service with any vpn provider. The other guides I tried, and advice I was given, on this board were very most likely good guides, and good advice. But being new to Ubuntu and a bit of a computer lout, I kept managing to foul things up, and just ended up more confused and frustrated, remaining unable to connect to a vpn. The five days it took PIA to help me were due to my own absolute unfamiliarity with Ubuntu, my talent for scrambling clear instructions, and the fact that I'd previously entered, and kept entering, wrong values in places hard to identify. Starting with a new re-format and install of Ubuntu 12.04, and by closely following the step-by-step instructions below that were provided by PIA, I was finally sucessful at accessing a vpn in just a few minutes with no more drama, and very little effort. It worked for me. It WILL work for you.

How to setup OpenVPN via Network Manager in Ubuntu 12.04 LTS

1. Open a Terminal, and run: 

sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome. 

This will prompt for both your password, and a Y/n answer, please provide it with your Ubuntu admin password, and Y then <enter>

2. Once installed, open System Settings, then Network

3. Press the + symbol to add a new connection, and select the VPN Interface, then press Create

4. Choose OpenVPN as your VPN Connection Type, and press Create

5. (The following is an example for Private Internet Access. Other providers will also supply these values from their service. Use them as needed below.)

    a. Gateway: Select one of the Hostnames's provided on PIA's site: [URL="https://www.privateinternetaccess.com/pages/network/"]https://www.privateinternetaccess.com/pages/network/
[/URL]
    b. Authentication

        1. Type: Password

        2. Username: The username provided with the PIA account

        3. Password: The password provided with the PIA account

        4. CA Certificate - This needs to be downloaded from the PIA site, download the following Zip file: [https://www.privateinternetaccess.com/openvpn/openvpn.zip](https://www.privateinternetaccess.com/openvpn/openvpn.zip) and extract the ca.crt file to     [/SIZE][/FONT][FONT=Candara][SIZE=3]somewhere[/SIZE][/FONT][FONT=Candara][SIZE=3] it won't be deleted. We suggest your Home folder. If you extract this to your home folder, when searching for it, please click on your username on the left side, which will take you right to the home folder, then select the ca.crt file from the options on the right.

    c. Advanced: In general, nothing will need to be set here, if there's a particular issue with your VPN, feel free to contact your provider for details and alternate setups that can be managed though Advanced

        1. PIA - Under Advanced, then General, check the "Use LZO data compression"

    d. IPv4 Settings

        1. Method: Automatic (VPN) Addresses Only

    2. DNS Servers: 8.8.8.8, 8.8.4.4, or your own favorite DNS servers, the ones provided are from Google.

6. Press Save. If you chose to have your password saved it may ask for you to verify your password to open your keyring.[/SIZE][/FONT]

---

