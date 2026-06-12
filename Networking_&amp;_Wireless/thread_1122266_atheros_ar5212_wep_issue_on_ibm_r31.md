---
title: "atheros ar5212 wep issue on ibm r31"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by Ryuhayabusa on 2009-04-10
hi guys,

i have an ar5212 pcmcia card 

lshw 
```

 *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ath0
       version: 01
       serial: 00:17:9a:02:5d:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.49 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

its running on madwifi drivers.

I was able to connect to my dlink router (g604) when i deactivated the WEP

Now i would like to run WEP with a shared key (i've heard open is more secure but i dunno if i can get my fathers vista computer to connect to an open WEP. But it is connected to the shared wep). Once wep is up i plan to specify in the router which mac addresses will be able to connect.

unfortunately i cannot get the atheros to connect.

iwlist ath0 scan gives 

```

 Cell 03 - Address: 00:22:B0:94:29:B6
                    ESSID:"jacqio"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200


```
so i guess i got good signal (i'm sitting next to it)

so i try

sudo iwconfig ath0 essid "jacqio" key ********

where i type the key in 10 digits of letters and numbers (letters were lower case)

and it works but then i get zero link quality in iwconfig 

 iwconfig 
```

lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"jacqio"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
i thought that i would get 59/94??

I'm on hardy 8.04, with 2.6.15 kernel. I'm using that kernel because people have been having problems with 2.6.24 kernel and r31.

any help is seriously appreciated.

Linux is fantastic except for hardware.

---

### Post by chili555 on 2009-04-10
Please try:```
sudo iwconfig ath0 essid "jacqio" key ******** [COLOR="Red"]restricted[/COLOR]
```

---

### Post by Ryuhayabusa on 2009-04-10
thanks for help chili. i always see you helping on this forum.

unfortunately same problem. still 0 link quality.

i'm sure that i'm putting the right key in because i have the other laptop working and my booster/wireless lan adapter (asus wl330)

i'll put up ifconfig because theres a weird adreSS for inet6

```

ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe02:5d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:4122 dropped:0 overruns:0 frame:4122
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:d8380000-d8390000 
eth0      Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e2ff:fe8c:71e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3738588 (3.5 MB)  TX bytes:358916 (350.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12000 (11.7 KB)  TX bytes:12000 (11.7 KB)


```

---

### Post by chili555 on 2009-04-11
Hmmmm!> ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0

eth0      Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
You are connected and have an IP address with your wired ethernet connection and now want to connect wirelessly, too? Your computer will have trouble doing that. I suggest you disconnect the wire and reboot and then troubleshoot your wireless.

---

### Post by Ryuhayabusa on 2009-04-11
hi chilli.

sorry i don't understand why I can't have both, they're on different IP adresses?

I pulled out the cable then 
i disables eth0 with 

sudo ifconfig eth0 down

and tried again

iwlist gave

```

ath0      Scan completed :
          Cell 01 - Address: 00:22:B0:94:29:B6
                    ESSID:"jacqio"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 02 - Address: 00:22:B0:94:29:B6
                    ESSID:"jacqio"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 03 - Address: 00:1C:DF:A2:4A:0A
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000


```

and 

sudo iwconfig ath0 essid "jacqio" key restricted *********

worked, i.e no error messages.

but after when i did iwconfig still had zero signal.and -95dB for the rssi and the other one.

It's probably becoming clear that I really don't know much about networking. I have hashed together this information from previous posts and guides on the forums.

I'll put my interfaces file in case something is wrong

```

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp



#auto eth0
iface eth0 inet static
address 192.168.1.48
netmask 255.255.255.0
gateway 192.168.1.254





#auto ath0
#iface ath0 inet static
#address 192.168.1.49
#netmask 255.255.255.0
#gateway 192.168.1.254
#wireless-key FF7AA7B47F
#wireless-essid jacqio

#the following is from the ubuntu guide http://ubuntuforums.org/showthread.php?t=202834
#
#
#auto ath0 
iface ath0 inet static
address 192.168.1.49
gateway 192.168.1.254
#dns-nameservers	
netmask 255.255.255.0
wireless-key FF******7F
wireless-essid jacqio
wpa-driver wext

```

And in the mean time i'll try to find out why i've got 2 jacqio's. Often they have slightly different Signal level's.

I'll also put the page from my router setup, this is probably redundant but I really want to solve the problem.

[HTML]
<html><head>
<meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"><script>var remote_user="admin"; </script>

<link rel="stylesheet" href="dlinkwirelesswebcm_files/common.css" type="text/css">
<script language="JavaScript"> var HistoryHref="home_dhcp.htm";
var HistoryItem="DHCP";

var Fimg1_1="<td width=11 valign=top height=49><img src=../html/images/"
var Fimg1_2=" width=11 height=49>";
var Fimg2_1="<td width=575 valign=top height=49><img src=../html/images/center_"
var Fimg2_2=".jpg width=575 height=49 usemap=#Map2 border=0></td>";
var Fimg3_1="<td width=20 valign=top height=49><img src=../html/images/"
var Fimg3_2=" width=19 height=49></td>";
var Flast="<td width=25 nowrap background=\"../html/images/right1.gif\"></td>";

var MTd1="<tr><td class="
var MTd2=" onclick=\"doLink('"
var MTd3="')\" vAlign=middle align=center width=133 height=60>";

var MTd="<tr><td BACKGROUND='../html/images/Title.gif' vAlign=middle align=center width=133 height=60>";

var Mfont1="<font color="
var Mfont2=" face=Arial><b>"
var Mfont3="</b></font></td></tr>";

var CHome = 1;
var CAdvanced = 2;
var CTools = 3;
var CStatus = 4;
var CHelp = 5;

var Amenu=new Array();

Amenu[0 ]=new Gitem(CHome, "Wizard", "/html/home/home_wizard.htm", 0);
Amenu[1 ]=new Gitem(CHome, "Wireless",    "/html/home/wireless.htm", 0);
Amenu[2 ]=new Gitem(CHome, "WAN",    "/html/home/home_wan.htm", 0);
Amenu[3 ]=new Gitem(CHome, "LAN",    "/html/home/home_lan.htm", 0);
Amenu[4 ]=new Gitem(CHome, "DHCP",   "/html/home/home_dhcp.htm", 0);
Amenu[5 ]=new Gitem(CHome, "DNS",    "/html/home/home_dns.htm", 0);
Amenu[6 ]=new Gitem(CHome, "Dynamic DNS",    "/html/home/ddns.htm", 0);
Amenu[7 ]=new Gitem(CHome, "Logout",  "/html/closeWin.html",	0); 

Amenu[8]=new Gitem(CAdvanced, "UPnP", "/html/advanced/adv_upnp.htm", 0);
Amenu[9]=new Gitem(CAdvanced, "Virtual Server", "/html/advanced/portforw.htm&var:pagename=fwan&var:category=categoryG", 0);
Amenu[10]=new Gitem(CAdvanced, "Lan Clients",    "/html/advanced/lanclients.htm", 0);
Amenu[11]=new Gitem(CAdvanced, "SNMP", "/html/advanced/adv_snmp.htm", 0);
Amenu[12]=new Gitem(CAdvanced, "TR069","/html/advanced/adv_acs.htm", 1);
Amenu[13]=new Gitem(CAdvanced, "Filters",        "/html/advanced/adv_filters.htm&var:rule=0", 0);
Amenu[14]=new Gitem(CAdvanced, "Bridge Filters",        "/html/advanced/adv_bfilters.htm&var:langrp=lan0", 0);
Amenu[15]=new Gitem(CAdvanced, "Routing", 		 "/html/advanced/adv_routing.htm&var:conid=", 0);
Amenu[16]=new Gitem(CAdvanced, "DMZ",            "/html/advanced/adv_dmz.htm", 0);
Amenu[17]=new Gitem(CAdvanced, "Parent Control",        "/html/advanced/adv_parentctl.htm", 0);
Amenu[18]=new Gitem(CAdvanced, "Firewall",       "/html/advanced/adv_firewall.htm", 0);
Amenu[19]=new Gitem(CAdvanced, "RIP", 			 "/html/advanced/adv_rip.htm", 0);
Amenu[20]=new Gitem(CAdvanced, "PPP", 			 "/html/advanced/adv_ppp.htm", 1);
Amenu[21]=new Gitem(CAdvanced, "ADSL", 	     "/html/advanced/adv_adsl.htm", 0);
Amenu[22]=new Gitem(CAdvanced, "ATM VCC", 		 "/html/advanced/adv_atmvcc.htm", 0);
Amenu[23]=new Gitem(CAdvanced, "QoS", "/html/advanced/adv_vlan.htm", 0);
Amenu[24]=new Gitem(CAdvanced, "Wireless<br>Management", 		 "/html/advanced/wireless_mang.htm", 0);
Amenu[25]=new Gitem(CAdvanced, "Wireless<br>Performance", 		 "/html/advanced/wireless_perf.htm", 0);
Amenu[26]=new Gitem(CAdvanced, "Logout",  "/html/closeWin.html",	0); 

Amenu[27]=new Gitem(CTools, "Admin", 	"/html/tools/tools_admin.htm", 0);
Amenu[28]=new Gitem(CTools, "Time", 	"/html/tools/tools_time.htm", 0);
Amenu[29]=new Gitem(CTools, "Remote Log", 	"/html/tools/tools_remotelog.htm", 0);
Amenu[30]=new Gitem(CTools, "System", 	"/html/tools/tools_system.htm", 0);
Amenu[31]=new Gitem(CTools, "Firmware", "/html/tools/tools_firmware.htm", 0);
Amenu[32]=new Gitem(CTools, "Miscellaneous", 	"/html/tools/tools_misc.htm", 0);
Amenu[33]=new Gitem(CTools, "Test", 	"/html/tools/tools_test.htm", 0);
Amenu[34]=new Gitem(CTools, "Logout",  "/html/closeWin.html",	0); 

Amenu[35]=new Gitem(CStatus, "Device Info", "/html/status/status_deviceinfo.htm", 0);
Amenu[36]=new Gitem(CStatus, "DHCP Clients", "/html/status/status_dhcpclients.htm", 0);
Amenu[37]=new Gitem(CStatus, "Log", 		"/html/status/status_log.htm", 0);
Amenu[38]=new Gitem(CStatus, "Statistics", 	"/html/status/status_statistics.htm", 0);
Amenu[39]=new Gitem(CStatus, "ADSL", 		"/html/status/status_adsl.htm", 0);
Amenu[40]=new Gitem(CStatus, "Logout",  "/html/closeWin.html",	0); 

Amenu[41]=new Gitem(CHelp, "Help", 		"/html/help/help.htm", 0);
Amenu[42]=new Gitem(CHelp, "Logout",  "/html/closeWin.html",	0); 
var g_FID=getFID();
function Gitem(ifolder,sname,surl,ishow)
{
    this.ifolder=ifolder;
    this.sname=sname;
    this.surl=surl;
    this.ishow=ishow;
}
function doLink(surl)
{
    shref ="../cgi-bin/webcm?getpage=.."+surl;
    document.location.href = shref;
}
function getFID()
{
    thisurl=document.location.href;
    PreSaveHref = top.GetHistoryHref();
//PreSaveHref = HistoryHref;
    temp =0;
	for(i=0;i<Amenu.length;i++)
	{
    	if(thisurl.indexOf(Amenu[i].surl)!=-1)
		{    		
    		temp=1;
    		return Amenu[i].ifolder;
    	}
	}
	if(temp == 0)
	{
		for(i=0;i<Amenu.length;i++)
    	{
	        if(Amenu[i].surl.indexOf(PreSaveHref)!=-1)
        	{
        		return Amenu[i].ifolder;
        	}
    	}
	}	
    return 1;
}
function Write_Folder_Images()
{
    g_FID=getFID();    
    if(g_FID==CHome)
    Fimg1=Fimg1_1+"head_over.jpg"+Fimg1_2
    else
    Fimg1=Fimg1_1+"head.jpg"+Fimg1_2
    
    Fimg2=Fimg2_1+g_FID+Fimg2_2
    
    if(g_FID==CHelp)
    Fimg3=Fimg3_1+"tail_over.jpg"+Fimg3_2
    else
    Fimg3=Fimg3_1+"tail.jpg"+Fimg3_2

    
    
    document.write(Fimg1);
    document.write(Fimg2);
    document.write(Fimg3);
    document.write(Flast);
}
function Write_Item_Images()
{
    var sstyle="style1";
    var sfont="#ffffff";
    thisurl=document.location.href;
    PreSaveItem = top.GetHistoryItem();
    //PreSaveItem = HistoryItem;

    document.write("<table border=0 cellpadding=0 cellspacing=0>");
    for(i=0;i<Amenu.length;i++)
    {
        //init
        
        if(Amenu[i].sname.length > 11)
        	//sfont="#ffffff SIZE=1";  modify by Jarry for string display size too small 2005/02/20
        	sfont="#ffffff SIZE=2";
        else
        	sfont="#ffffff SIZE=2";
        	
        bgimg=" BACKGROUND='../html/images/Title.gif'"
        if(Amenu[i].ifolder==g_FID && !Amenu[i].ishow)
        {
            if((Amenu[i].sname == PreSaveItem))
            {            	
            	
                if(Amenu[i].sname.length > 11)
                	//sfont="#000000 SIZE=1"; modify by Jarry for string display size too small 2005/02/20
                	sfont="#000000 SIZE=2";
                else
                	sfont="#000000 SIZE=2";
                
                
                bgimg=" BACKGROUND='../html/images/Title_over.gif'"
                
            }
		//alert(Amenu[i].sname+" : "+sstyle);
            document.write(MTd1+sstyle+bgimg+MTd2+Amenu[i].surl+MTd3);       
            //document.write(MTd);
            document.write(Mfont1+sfont+Mfont2+Amenu[i].sname+Mfont3);
        }
        
    }
    document.write("<tr><td><img src=../html/images/sp.gif width=140 heigh=10 ></td></tr></table>");
}

function doHelp()
{
	doLink('/html/help/help.htm');
}

function mainTableStart()
{
	document.write('<table width=795 border=0 cellspacing=0 cellpadding=0 align=center>') ;
}

function MapContent()
{
	document.write('<map name=Map1>'+
	'<area shape=rect coords=20,9,153,64 >'+
	'</map><map name=Map2>'+
	'<area shape="rect" coords="22,18,92,42" href="../cgi-bin/webcm?getpage=../html/home/home_wizard.htm" target="_self" alt="home">'+
	'<area shape="rect" coords="123,18,225,42" href="../cgi-bin/webcm?getpage=../html/advanced/adv_upnp.htm" target="_self" alt="adv">'+
	'<area shape="rect" coords="256,18,321,42" href="../cgi-bin/webcm?getpage=../html/tools/tools_admin.htm" target="_self" alt="tools">'+
	'<area shape="rect" coords="378,18,448,42" href="../cgi-bin/webcm?getpage=../html/status/status_deviceinfo.htm" target="_self" alt="status">'+
	'<area shape="rect" coords="496,18,556,42" href="../cgi-bin/webcm?getpage=../html/help/help.htm" target="_self" alt="help">'+
	'</map>');
}
function logo()
{
	document.write('<tr><td colspan=6 nowrap width=100%><div align=left><img src=../html/images/logo.jpg width="795" height="95" usemap=#Map1 border=0></div></td></tr>') ;
}
//To align table :alanis
function Write_Folder_Images1()
{
    document.write("<tr><td width=11 valign=top height=21>&nbsp;</td>");
    document.write("<td width=575 valign=top height=21>&nbsp;</td>");
    document.write("<td width=\"19\" height=21 background=../html/images/right2.gif>&nbsp;</td>");
    document.write("<td width=25 nowrap height=21 background=\"../html/images/right1.gif\">&nbsp;</td></tr>");
}
function secondRow()
{
/* RT_EN
	document.write('<tr><td align=center width=140 height=40><IMG height=49 src="../html/images/device.gif" width=140 border=0></td>');
	document.write('<td rowspan="2" width="25" nowrap height=100% background=../html/images/sp_line.jpg><img src="../html/images/sp.gif" width=25 heigh="10"></td>') ;
	Write_Folder_Images();
	document.write('</tr>');
*/
	document.write('<tr><td rowspan="2" align=center width=140 height=70 bgColor=#c1cece><IMG src="../html/images/device.gif" width=140 height=70 border=0></td>');
	document.write('<td rowspan="3" width="25" nowrap height=100% background=../html/images/sp_line.jpg><img src="../html/images/sp.gif" width=25 heigh="10"></td>') ;
	Write_Folder_Images();
	document.write('</tr>');
	Write_Folder_Images1();
}
function ThirdRowStart()
{
	document.write('<tr><td valign=top bgColor=#c1cece>'+
					'<table border=0 width=100% valign=top cellspacing=0 cellpadding=0 bgcolor=#C1CECE>'+
					'<tr><td width=140 valign=top bgcolor=#C1CECE>');
}
function ThirdRowEnd()
{
	document.write('</td></tr></table></td>') ;
}
function inTableStart()
{
	document.write('<td colspan=2 bgcolor=#FFFFFF valign=top align=center>') ;
}
function inTableEnd()
{
	document.write('</td>') ;
}
function mainTableEnd()
{
	document.write('<td width="19" height=100% background=../html/images/right2.gif><img src="../html/images/sp.gif" width=19 heigh="10"></td>'+
					'<td width="25" height=100% background=../html/images/right1.gif><img src="../html/images/sp.gif" width=25 heigh="10"></td>'+
					'</tr>'+
					'<tr>'+
					'<td height="44" width=100% background=../html/images/last1.jpg>&nbsp;</td>'+
					'<td height="44" width=100% background=../html/images/last2.jpg>&nbsp;</td>'+
					'<td colSpan=2 height="44" width=100% background=../html/images/last3.jpg>&nbsp;</td>'+
					'<td colspan=2 height="44" width=25 background=../html/images/last4.jpg>&nbsp;</td>'+
					'</tr>'+
					'</table>');
}
function uiDoHelp()
{
  document.location.href="../cgi-bin/webcm?getpage=../html/help/help.htm";
}
</script>
<script language="JavaScript" src="dlinkwirelesswebcm_files/jsl.js"></script>
<script language="JavaScript" src="dlinkwirelesswebcm_files/val.js"></script>
<script language="JavaScript" src="dlinkwirelesswebcm_files/error.js"></script>
<script>
function uiDoNone(){
  if(remote_user=="user")
   {
      alert("sorry, you're not authorised to modify this page.");
      return false;
   }
  document.getElementById("uiSecurityForm").method="GET";
  document.getElementById("uiPostGetPage").value="../html/home/wireless_none.htm";
  document.getElementById("uiSecurityForm").submit();
}
function uiDoWEP(){
  if(remote_user=="user")
   {
      alert("sorry, you're not authorised to modify this page.");
      return false;
   }
  document.getElementById("uiSecurityForm").method="GET";
  document.getElementById("uiPostGetPage").value="../html/home/wireless_security_wep.htm";
  document.getElementById("uiSecurityForm").submit();
}
function uiDoWPA(){
  if(remote_user=="user")
   {
      alert("sorry, you're not authorised to modify this page.");
      return false;
   }
  document.getElementById("uiSecurityForm").method="GET";
  document.getElementById("uiPostGetPage").value="../html/home/wireless_security_wpa.htm";
  document.getElementById("uiSecurityForm").submit();
}
function uiDo8021x(){
  if(remote_user=="user")
   {
      alert("sorry, you're not authorised to modify this page.");
      return false;
   }
  document.getElementById("uiSecurityForm").method="GET";
  document.getElementById("uiPostGetPage").value="../html/home/wireless_security_8021x.htm";
  document.getElementById("uiSecurityForm").submit();
}
</script>
<script>
// wireless_wep.js //begin
var sec_profile = new Array();

function uiDoValidate_WEP(){
   if(remote_user=="user")
   {
  	alert("sorry, you're not authorised to modify this page.");
  	return false;
   }     
   var wep_enabled = parseInt(document.getElementById("uiPostWepEnabled").value);

   if ((wep_enabled == 1) && (document.getElementById("uiPostKeyValue1").value.length == 0)&&(document.getElementById("uiPostKeyValue2").value.length == 0) && (document.getElementById("uiPostKeyValue3").value.length == 0) &&(document.getElementById("uiPostKeyValue4").value.length == 0)){
      alert("Enter WEP Keys");
      return false;
   }
   if (document.getElementById("uiPostKeyValue1").value.length == 0){
      jslDisable("uiPostKeyValue1");	
   }
   if (document.getElementById("uiPostKeyValue2").value.length == 0){
      jslDisable("uiPostKeyValue2");	
   }
   if (document.getElementById("uiPostKeyValue3").value.length == 0){
      jslDisable("uiPostKeyValue3");	
   }
   if (document.getElementById("uiPostKeyValue4").value.length == 0){
      jslDisable("uiPostKeyValue4");	
   }

   //alert ("Privacy type is set to WEP. Multiple SSID support will be disabled");
   return true;
}
function uiDoOnLoad_WEP()
{
    var i=0;

   sec_profile[i++]=2;sec_profile[i++]=0;sec_profile[i++]=0;sec_profile[i++]=0;
   //jslPostToViewCheckBox("uiViewWepEnabled","uiPostWepEnabled");//by Maurice
   document.getElementById("uiPostAuthType").value = uiDoShowAuthType(document.getElementById("uiPostAuthType").value); 
   uiSelectValue("uiViewKeyId", document.getElementById("uiPostKeyId").value, 4);
   jslSetValue("uiViewKeyValue1", "uiPostKeyValue1"); 
   document.getElementById("uiPostKeyLen1").value = uiDoShowKeyLen("uiViewKeyLen1", document.getElementById("uiPostKeyLen1").value); 
   jslSetValue("uiViewKeyValue2", "uiPostKeyValue2"); 
   document.getElementById("uiPostKeyLen2").value = uiDoShowKeyLen("uiViewKeyLen2", document.getElementById("uiPostKeyLen2").value); 
   jslSetValue("uiViewKeyValue3", "uiPostKeyValue3"); 
   document.getElementById("uiPostKeyLen3").value = uiDoShowKeyLen("uiViewKeyLen3", document.getElementById("uiPostKeyLen3").value); 
   jslSetValue("uiViewKeyValue4", "uiPostKeyValue4"); 
   document.getElementById("uiPostKeyLen4").value = uiDoShowKeyLen("uiViewKeyLen4", document.getElementById("uiPostKeyLen4").value); 
}

function isAsciiStringNum(string,bitvalue)
{
	var Result;
	if(string =="")
	{
		return true;
	}	
	if(bitvalue == 0)
	{
		//Result = string.match("^([0-9,A-F,a-f]{2}[ ]{1}){4}[0-9,A-F,a-f]{2}$");
		Result = string.match("^([0-9,A-F,a-f]{2}){4}[0-9,A-F,a-f]{2}$");
		if(Result == null)
		{
			alert("The Encryption Key must be 10 hexadecimal digits.");
			return false;
		}
	}
	else if(bitvalue == 1)
	{
		//Result = string.match("^([0-9,A-F,a-f]{2}[ ]{1}){12}[0-9,A-F,a-f]{2}$");
		Result = string.match("^([0-9,A-F,a-f]{2}){12}[0-9,A-F,a-f]{2}$");
		if(Result == null)
		{
			alert("The Encryption Key must be 26 hexadecimal digits.");
			return false;
		}
	}
	else
	{
		//Result = string.match("^([0-9,A-F,a-f]{2}[ ]{1}){25}[0-9,A-F,a-f]{2}$");
		Result = string.match("^([0-9,A-F,a-f]{2}){28}[0-9,A-F,a-f]{2}$");
		if(Result == null)
		{
			alert("The Encryption Key must be 58 hexadecimal digits.");
			return false;
		}
	}
  return true;
}

function uiDoSave_WEP(){
   
   if(remote_user=="user")
   {
  	alert("sorry, you're not authorised to modify this page.");
  	return false;
   }     
   jslViewToPostCheckBox("uiPostAPEnabled", "uiViewAPEnabled");
   jslSetValue("uiPostSSID", "uiViewSSID");
   jslSetValue("uiPostFwdSSID", "uiViewSSID");
   jslSetValue("uiPostChannel", "uiViewChannel");
   jslSetValue("uiPostFwdChannel","uiViewChannel");
   jslSetValue("uiPostVlanID", "uiViewVlanID");
   jslSetValue("uiPostAddPriority", "uiViewAddPriority");
   //sean //TYLinuxV3_G624T //2006/2/23 17:49 //begin
   //Not setting wbd0 if the VLAN ID is 0. (Because there is no wbd interface)
    if(document.getElementById("uiPostVlanID").value == 0){
        jslDisable("uiPostWbVlanID");
        jslDisable("uiPostWbPBit0");
    }else{
	jslSetValue("uiPostWbVlanID", "uiViewVlanID");
	jslSetValue("uiPostWbPBit0", "uiViewAddPriority");
    }
   //sean //TYLinuxV3_G624T //2006/2/23 17:49 //end
   
   document.getElementById("uiPostPrivacyType").value = 2;
   //jslViewToPostCheckBox("uiPostWepEnabled", "uiViewWepEnabled");//by Maurice.
   jslSetValue("uiPostKeyValue1", "uiViewKeyValue1");
   jslSetValue("uiPostKeyValue2", "uiViewKeyValue2");
   jslSetValue("uiPostKeyValue3", "uiViewKeyValue3");
   jslSetValue("uiPostKeyValue4", "uiViewKeyValue4");

	if(isAsciiStringNum(document.getElementById("uiViewKeyValue1").value,document.getElementById("uiViewKeyLen1").selectedIndex) == false)
	{
		document.getElementById("uiViewKeyValue1").focus();
		return false;
	}
	if(isAsciiStringNum(document.getElementById("uiViewKeyValue2").value,document.getElementById("uiViewKeyLen2").selectedIndex) == false)
	{
		document.getElementById("uiViewKeyValue2").focus();
		return false;
	}
	if(isAsciiStringNum(document.getElementById("uiViewKeyValue3").value,document.getElementById("uiViewKeyLen3").selectedIndex) == false)
	{
		document.getElementById("uiViewKeyValue3").focus();
		return false;
	}
	if(isAsciiStringNum(document.getElementById("uiViewKeyValue4").value,document.getElementById("uiViewKeyLen4").selectedIndex) == false)
	{
		document.getElementById("uiViewKeyValue4").focus();
		return false;
	}	
   //add by Maurice
   document.getElementById("uiPostWepEnabled").value = 1;
	
   if( (uiDoValidate()==true) && (uiDoValidate_WEP()==true) )
      jslFormSubmit("uiPostWEPForm");
   return;
}


function uiChangeAuthType(arg)
{
  document.getElementById("uiPostAuthType").value = arg;
}

function uiDoShowAuthType(value)
{
  var i;
  var selector = document.getElementById("uiViewAuthType");
  if(selector==null) return;

  for(i=0; i < selector.length; i++)
  {
    if(selector.options[i].value == value)
	{
      selector.selectedIndex = i;
	  return(value);
	}
  }
  return(selector.options[0].value);
}

function uiChangeKeyLen(id, arg)
{
   document.getElementById(id).value = arg;
}

function uiDoShowKeyLen(id, value)
{
   var i;
   var selector = document.getElementById(id);

   if(selector==null)
      return;

   for(i=0; i < selector.length; i++){
      if(selector.options[i].value == value){
         selector.selectedIndex = i;
         selector.selected=true;
 	 return(value);
      }
   }
   selector.selectedIndex = 0;
   return(selector.options[0].value);
}

function uiSelectValue(id, value, max)
{
	jslDoToggleRadio(id, value, max);
}

function uiDoSelectWepKeyId(arg)
{
	document.getElementById("uiPostKeyId").value = arg;
//	alert("radio: "+arg);
}

function uiDoSaveAPEnable()
{
	if(document.getElementById("uiViewAPEnabled").value=="on")
	{
		document.getElementById("uiViewAPEnabled").checked=false;
		document.getElementById("uiViewAPEnabled").value="off";
	}
	else
	{
	document.getElementById("uiViewAPEnabled").checked=true;
	document.getElementById("uiViewAPEnabled").value="on";
	}
	jslViewToPostCheckBox("uiPostAPEnabled", "uiViewAPEnabled");
   jslFormSubmit("uiPostAPForm");
}
// wireless_wep.js //end</script>
<script>
//sean //20060119 20:53 //for counting used mssid number
var numSSIDList;
var MSSIDenabled;
var SSIDList = new Array(10);
var ssid0_vlan_id;      //for alert when used mssid & ssid0_vlan==0
var wdsmode;            //for alert about WDS

function uiDoOnLoad()
{
   jslPostToViewCheckBox("uiViewAPEnabled","uiPostAPEnabled");
   document.getElementById("uiPostChannel").value = uiSelect("uiViewChannel", document.getElementById("uiPostChannel").value);  
//   jslSetValue("uiViewSSID","uiPostSSID");
   document.getElementById("uiViewSSID").value = decrypt(document.getElementById("uiPostSSID").value);

//   alert("837476908288");

    //sean //TYLinuxV3_G624T //20060113
    //VLAN ID
    document.getElementById("uiViewVlanID").value = document.getElementById("uiPostVlanID").value;
    //Priority
    document.getElementById("uiViewAddPriority").value = document.getElementById("uiPostAddPriority").value;
   
   //sean //TYLinuxV3_G624T //20060119 20:53 //for counting the number of used mssid 
   for ( i=0; i< 10; i++)
      SSIDList[ i ] = 0;
   i = 0;
   SSIDList[i++]='0';
   numSSIDList = i;
   MSSIDenabled = 0;
   ssid0_vlan_id = 0;
   wdsmode = 3;
}
function decrypt(str)
{
	var result = "";
	var num;
	for(i = 0; i < str.length; i += 2)
	{
		num = parseInt(str.substr(i,[2])) + 23;
		num = unescape('%' + num.toString(16));
		result += num;
	}
	return unescape(result);
}
function encrypt(str)
{
	var result = "";
	var	escaped;

	escaped = escape(str);
	for(i = 0; i < escaped.length; i++)
		result += escaped.charCodeAt(i) - 23;
	return result;
}
function uiDoValidate()
{
	if(remote_user=="user")
         {
  	     alert("sorry, you're not authorised to modify this page.");
  	     return false;
         }
	var output;
	if (document.getElementById("uiPostSSID").value.length == 0)
	{
		alert ("Invalid SSID");
		return false;
	}	
	else
	{
		output = encrypt(document.getElementById("uiPostSSID").value);
		document.getElementById("uiPostSSID").value = output;
	}
   
   //sean //G624T //2006/1/20 10:57 //begin
	if (valDoValidateInteger(document.getElementById("uiPostVlanID").value) 
	    != null)
	{
	  alert ("Invalid VLAN ID");
	  return false;
	}
   //if (document.getElementById("uiPostVlanID").value  != 0 && numSSIDList == 1 ){
   if (document.getElementById("uiPostVlanID").value  != 0 && MSSIDenabled == 0 ){
	   alert("Multiple SSID support is disabled. Cannot configure VLAN to be non-zero.");
	   document.getElementById("uiPostVlanID").value = 0;
	   return false;
	}
   if (MSSIDenabled == 1){
      if (document.getElementById("uiPostVlanID").value < 1 ||
          document.getElementById("uiPostVlanID").value > 4095 ){  
         alert ("SSID Vlan range is [1, 4095]");
         return false;
      }
   }
    
   if (document.getElementById("uiPostAddPriority").value < 0 ||
       document.getElementById("uiPostAddPriority").value > 7 )
   {
       alert ("SSID Priority range is [0, 7]");
       return false;
   }
   //sean //G624T //2006/1/20 10:57 //end
   
   return true;
}
function uiDoSave()
{
   if(remote_user=="user")
   {
  	alert("sorry, you're not authorised to modify this page.");
  	return false;
   }     
   jslViewToPostCheckBox("uiPostAPEnabled", "uiViewAPEnabled");
   jslSetValue("uiPostSSID", "uiViewSSID");
   jslSetValue("uiPostFwdSSID", "uiViewSSID");
   jslSetValue("uiPostChannel", "uiViewChannel");
   jslSetValue("uiPostFwdChannel","uiViewChannel");
   
    //sean //TYLinuxV3_G624T //2006/1/20 10:02 //begin
    //VLAN ID
   jslSetValue("uiPostVlanID", "uiViewVlanID");
   jslSetValue("uiPostFwdVlanID", "uiViewVlanID");
   //Priority
   jslSetValue("uiPostAddPriority", "uiViewAddPriority");
   jslSetValue("uiPostFwdPriority", "uiViewAddPriority");
   //sean //TYLinuxV3_G624T //2006/1/20 10:02 //end 
   //sean //TYLinuxV3_G624T //2006/2/23 17:49 //begin
   //Not setting wbd0 if the VLAN ID is 0. (Because there is no wbd interface)
    if(document.getElementById("uiPostVlanID").value == 0){
        jslDisable("uiPostWbVlanID");
        jslDisable("uiPostWbPBit0");
    }else{
	jslSetValue("uiPostWbVlanID", "uiViewVlanID");
	jslSetValue("uiPostWbPBit0", "uiViewAddPriority");
    }
   //sean //TYLinuxV3_G624T //2006/2/23 17:49 //end
    
   if(uiDoValidate()==true)
      jslFormSubmit("uiPostForm");

   return;
}
function uiDoAPEnable(){
   if(document.getElementById("uiViewAPEnabled").value=="on"){
      document.getElementById("uiViewAPEnabled").checked=false;
      document.getElementById("uiViewAPEnabled").value="off";
//      jslDisable("uiPostAPEnabled");
//      jslDisable("uiPostChannel");
//      jslDisable("uiPostSSID");
   }else{
      document.getElementById("uiViewAPEnabled").checked=true;
      document.getElementById("uiViewAPEnabled").value="on";
//      jslEnable("uiPostAPEnabled");
//      jslEnable("uiPostChannel");
//      jslEnable("uiPostSSID");
   }
      
   return;
}
function uiChangeChannel(value){
  document.getElementById("uiPostChannel").value = value;
}
function uiSelect(id, value)
{
  var i;
  var selector = document.getElementById(id);
  if(selector==null) return;
	
  for(i=0; i < selector.length; i++)
  {
    if(selector.options[i].value == value)
	{
          selector.selectedIndex = i;
	  return(value);
	}
  }
  return(selector.options[0].value);
}
function uiDoCancel()
{     
     document.location.href="../cgi-bin/webcm?getpage=../html/home/wireless.htm";
}
</script>
<script language="JavaScript">
top.HistoryHref="wireless.html";
top.HistoryItem="Wireless";
</script> 
</head><body onload="uiDoOnLoad();uiDoOnLoad_WEP()">
<script type="text/javascript">
	mainTableStart();
	MapContent();
	logo();
	secondRow();
	ThirdRowStart();
	Write_Item_Images();//left area
	ThirdRowEnd();
	inTableStart();
</script><map name="Map1"><area shape="rect" coords="20,9,153,64"></map><map name="Map2"><area shape="rect" coords="22,18,92,42" href="http://router/cgi-bin/webcm?getpage=../html/home/home_wizard.htm" target="_self" alt="home"><area shape="rect" coords="123,18,225,42" href="http://router/cgi-bin/webcm?getpage=../html/advanced/adv_upnp.htm" target="_self" alt="adv"><area shape="rect" coords="256,18,321,42" href="http://router/cgi-bin/webcm?getpage=../html/tools/tools_admin.htm" target="_self" alt="tools"><area shape="rect" coords="378,18,448,42" href="http://router/cgi-bin/webcm?getpage=../html/status/status_deviceinfo.htm" target="_self" alt="status"><area shape="rect" coords="496,18,556,42" href="http://router/cgi-bin/webcm?getpage=../html/help/help.htm" target="_self" alt="help"></map><table width="795" align="center" border="0" cellpadding="0" cellspacing="0"><tbody><tr><td colspan="6" width="100%" nowrap="nowrap"><div align="left"><img src="dlinkwirelesswebcm_files/logo.jpg" usemap="#Map1" width="795" border="0" height="95"></div></td></tr><tr><td rowspan="2" width="140" align="center" bgcolor="#c1cece" height="70"><img src="dlinkwirelesswebcm_files/device.gif" width="140" border="0" height="70"></td><td rowspan="3" width="25" background="dlinkwirelesswebcm_files/sp_line.jpg" height="100%" nowrap="nowrap"><img src="dlinkwirelesswebcm_files/sp.gif" heigh="10" width="25"></td><td valign="top" width="11" height="49"><img src="dlinkwirelesswebcm_files/head_over.jpg" width="11" height="49"></td><td valign="top" width="575" height="49"><img src="dlinkwirelesswebcm_files/center_1.jpg" usemap="#Map2" width="575" border="0" height="49"></td><td valign="top" width="20" height="49"><img src="dlinkwirelesswebcm_files/tail.jpg" width="19" height="49"></td><td width="25" background="dlinkwirelesswebcm_files/right1.gif" nowrap="nowrap"></td></tr><tr><td valign="top" width="11" height="21">&nbsp;</td><td valign="top" width="575" height="21">&nbsp;</td><td width="19" background="dlinkwirelesswebcm_files/right2.gif" height="21">&nbsp;</td><td width="25" background="dlinkwirelesswebcm_files/right1.gif" height="21" nowrap="nowrap">&nbsp;</td></tr><tr><td valign="top" bgcolor="#c1cece"><table valign="top" width="100%" bgcolor="#c1cece" border="0" cellpadding="0" cellspacing="0"><tbody><tr><td valign="top" width="140" bgcolor="#c1cece"><table border="0" cellpadding="0" cellspacing="0"><tbody><tr><td class="style1" onclick="doLink('/html/home/home_wizard.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>Wizard</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/home/wireless.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title_over.gif" height="60"><font size="2" color="#000000" face="Arial"><b>Wireless</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/home/home_wan.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>WAN</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/home/home_lan.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>LAN</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/home/home_dhcp.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>DHCP</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/home/home_dns.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>DNS</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/home/ddns.htm')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>Dynamic DNS</b></font></td></tr><tr><td class="style1" onclick="doLink('/html/closeWin.html')" valign="middle" width="133" align="center" background="dlinkwirelesswebcm_files/Title.gif" height="60"><font size="2" color="#ffffff" face="Arial"><b>Logout</b></font></td></tr><tr><td><img src="dlinkwirelesswebcm_files/sp.gif" heigh="10" width="140"></td></tr></tbody></table></td></tr></tbody></table></td><td colspan="2" valign="top" align="center" bgcolor="#ffffff">

<form action="webcm" id="uiSecurityForm" target="_self" onsubmit="return false">
   <input name="getpage" value="../html/home/wireless_none.htm" id="uiPostGetPage" type="hidden">
   <table width="540" align="center" border="0" bordercolor="#000000" cellpadding="6" cellspacing="0">
      <tbody><tr>
         <td class="tabhead" colspan="2" align="left" height="15">
            <strong>Wireless Settings</strong>
         </td>
      </tr>
      <tr>
         <td class="tabdata" colspan="2" align="left" height="15">
            These are the wireless settings for the AP(Access Point) Portion.
         </td>
      </tr>
      <tr><!-- Enable AP -->
         <td class="tabdata" align="right" height="15">
            &nbsp;
         </td>
         <td class="tabdata" align="left">
            <input value="on" name="APEnable" id="uiViewAPEnabled" onclick="uiDoAPEnable()" type="checkbox">Enable AP
         </td>
      </tr>
      <tr><!-- SSID -->
         <td class="tabdata" align="right" height="15">
            SSID:
         </td>
         <td class="tabdata" align="left">
            <input class="tabdata" name="SSIDName" id="uiViewSSID" type="text">
         </td>
      </tr>
      <tr><!-- VLAN ID -->
         <td class="tabdata" align="right" height="15">
            VLAN ID:
         </td>
         <td class="tabdata" align="left">
            <input class="tabdata" name="VlanIDName" id="uiViewVlanID" value="0" maxlength="4" size="5" type="text">
         </td>
      </tr>
      <tr><!-- Priority -->
         <td class="tabdata" align="right" height="15">
            Priority:
         </td>
         <td class="tabdata" align="left">
            <input class="tabdata" name="AddPriorityName" id="uiViewAddPriority" value="0" maxlength="1" size="5" type="text">
         </td>
      </tr>
      <tr><!-- Channel -->
         <td class="tabdata" align="right" height="15">
            Channel:
         </td>
         <td class="tabdata" align="left">
            <select class="tabdata" name="Channel" id="uiViewChannel" onchange="uiChangeChannel(value)">
               <option value="1">1
               </option><option value="2">2
               </option><option value="3">3
               </option><option value="4">4
               </option><option value="5">5
               </option><option value="6">6
               </option><option value="7">7
               </option><option value="8">8
               </option><option value="9">9
               </option><option value="10">10
               </option><option value="11">11
            </option><option value="12">12
	                    </option><option value="13">13
                   
               
            
            
            </option></select>
         </td>
      </tr>

      <tr>
         <td class="tabdata" align="right" height="15">
            Security:
         </td>
         <td class="tabdata" align="left">
            <input value="1" name="APSecurity" id="uiViewAPSecurity0" onclick="uiDoNone()" type="radio">None
            <input value="2" name="APSecurity" id="uiViewAPSecurity1" checked="checked" onclick="uiDoWEP()" type="radio">WEP
            <input value="3" name="APSecurity" id="uiViewAPSecurity2" onclick="uiDoWPA()" type="radio">WPA
            <input value="4" name="APSecurity" id="uiViewAPSecurity3" onclick="uiDo8021x()" type="radio">802.1x
         </td>
      </tr>
		<tr>
         <td colspan="2"><img src="dlinkwirelesswebcm_files/gray.gif" width="530" border="0" height="1"></td>
      </tr>
      <tr>
         <td colspan="2">
            <table width="530" align="center" border="0" bordercolor="#000000" cellpadding="8" cellspacing="0">
	       <!-- //marked by Maurice
               <tr>
                  <td class=tabdata align=left colspan=3>
                     <input type=checkbox id=uiViewWepEnabled onclick=jslDoToggleCheckBox(id)>Enable WEP Wireless Security
                  </td>
               </tr>
	       -->
               <tbody><tr>
                  <td class="tabdata" colspan="3" align="left">
                     Authentication Type:
                     <select class="tabdata" onchange="uiChangeAuthType(value)" id="uiViewAuthType">
                        <option value="0">Open</option>
                        <option value="1">Shared</option>
                        <option value="2">Both</option>
                     </select>
                  </td>
               </tr>
               <tr>
                  <td class="newtabdata" width="30">
                     Select
                  </td>
                  <td class="newtabdata" width="450">
                     Encryption Key
                  </td>
                  <td class="newtabdata" width="50">
                     Cipher
                  </td>
               </tr>
               <tr>
                  <td class="newtabdata" width="30">
                     <input value="on" name="uiWEPSelect" id="uiViewKeyId0" onclick="jslDoToggleRadio('uiViewKeyId',0,4);uiDoSelectWepKeyId(0)" type="radio">
                  </td>
                  <td class="newtabdata" width="450">
                     <input class="tabdata" size="50" maxlength="86" id="uiViewKeyValue1" type="password">
                  </td>
                  <td class="newtabdata" width="50">
                     <select class="tabdata" id="uiViewKeyLen1" onchange='uiChangeKeyLen("uiPostKeyLen1",value)'>
                        <option value="5">64  bits</option>
                        <option value="13">128 bits</option>
                        <option value="29">256 bits</option>
                     </select>
                  </td>
               </tr>               
               <tr>
                  <td class="newtabdata" width="30">
                     <input value="off" name="uiWEPSelect" id="uiViewKeyId1" onclick="jslDoToggleRadio('uiViewKeyId',1,4);uiDoSelectWepKeyId(1)" type="radio">
                  </td>
                  <td class="newtabdata" width="450">
                     <input class="tabdata" size="50" maxlength="86" id="uiViewKeyValue2" type="password">
                  </td>
                  <td class="newtabdata" width="50">
                     <select class="tabdata" id="uiViewKeyLen2" onchange='uiChangeKeyLen("uiPostKeyLen2",value)'>
                        <option value="5">64  bits</option>
                        <option value="13">128 bits</option>
                        <option value="29">256 bits</option>
                     </select>
                  </td>
               </tr>
               <tr>
                  <td class="newtabdata" width="30">
                     <input value="off" name="uiWEPSelect" id="uiViewKeyId2" onclick="jslDoToggleRadio('uiViewKeyId',2,4);uiDoSelectWepKeyId(2)" type="radio">
                  </td>
                  <td class="newtabdata" width="450">
                     <input class="tabdata" size="50" maxlength="86" id="uiViewKeyValue3" type="password">
                  </td>
                  <td class="newtabdata" width="50">
                     <select class="tabdata" id="uiViewKeyLen3" onchange='uiChangeKeyLen("uiPostKeyLen3",value)'>
                        <option value="5">64  bits</option>
                        <option value="13">128 bits</option>
                        <option value="29">256 bits</option>
                     </select>
                  </td>
               </tr>
               <tr>
                  <td class="newtabdata" width="30">
                     <input value="off" name="uiWEPSelect" id="uiViewKeyId3" onclick="jslDoToggleRadio('uiViewKeyId',3,4);uiDoSelectWepKeyId(3)" type="radio">
                  </td>
                  <td class="newtabdata" width="450">
                     <input class="tabdata" size="50" maxlength="86" id="uiViewKeyValue4" type="password">
                  </td>
                  <td class="newtabdata" width="50">
                     <select class="tabdata" id="uiViewKeyLen4" onchange='uiChangeKeyLen("uiPostKeyLen4",value)'>
                        <option value="5">64  bits</option>
                        <option value="13">128 bits</option>
                        <option value="29">256 bits</option>
                     </select>
                  </td>
               </tr>
               <tr>
                  <td class="tabdata" colspan="3" align="left">
                     Enter 10, 26, 58 hexadecimal digits(0~9,A~F)  for 64, 128, or 256 bit Encryption Keys respectively. 
                     e.g., AAAAAAAAAA for a key length of 64 bits.
                  </td>
               </tr>

               
            </tbody></table>
         </td>
      </tr>
      
      <tr>
         <td colspan="2">
         </td>
      </tr>
	<tr>
        <td class="tabdata" colspan="2" align="left" height="15">
          
         Please save and reboot the device to take effect !
        </td>
     </tr>      
	<tr>
		<td colspan="2" align="right">
		<input name="image" src="dlinkwirelesswebcm_files/apply_p.jpg" onclick="uiDoSave_WEP()" id="uiViewApply" type="image" border="0">
		<input name="image" src="dlinkwirelesswebcm_files/cancel_p.jpg" onclick="uiDoCancel()" id="uiViewCancel" type="image" border="0">
		<input name="image" src="dlinkwirelesswebcm_files/help_p.jpg" onclick="uiDoHelp()" type="image" border="0">
		</td>
	</tr>      
   </tbody></table>
</form>

<form name="uiPostForm" action="webcm" target="_self" method="post" id="uiPostWEPForm">
   <input name="getpage" value="../html/home/wireless_security_wep.htm" type="hidden">
   <input name="ap:settings/ap_enabled" value="1" id="uiPostAPEnabled" type="hidden">
   <input name="ap:settings/ssid0/ssid" value="837476908288" id="uiPostSSID" type="hidden">
   <input name="ap:settings/channel_g" value="8" id="uiPostChannel" type="hidden">
   <input name="var:apenabled" value="" id="uiPostFwdEnabled" type="hidden">
   <input name="var:ssid" value="" id="uiPostFwdSSID" type="hidden">
   <input name="var:channel" value="" id="uiPostFwdChannel" type="hidden">
   <input name="ap:settings/user_isolation" value="0" id="uiPostUserIsolation" type="hidden">
   <!-- //TYLinuxV3_G624T //sean //2006/1/20 10:08 //begin -->
   <input name="ap:settings/ssid0/vlan" value="0" id="uiPostVlanID" type="hidden">
   <input name="ap:settings/ssid0/priority" value="0" id="uiPostAddPriority" type="hidden">
   <input name="var:vlanid" value="" id="uiPostFwdVlanID" type="hidden">
   <input name="var:priority" value="" id="uiPostFwdPriority" type="hidden">
   <!-- //TYLinuxV3_G624T //sean //2006/1/20 10:08 //end -->
   <!-- //TYLinuxV3_G624T //sean //2006/2/23 17:42 //begin -->
   <input name="wbd0:settings/vlan_id" value="" id="uiPostWbVlanID" type="hidden">
   <input name="wbd0:settings/priority_bit" value="" id="uiPostWbPBit0" type="hidden">
   <!-- //TYLinuxV3_G624T //sean //2006/2/23 17:42 //end -->

   <!--WEP security settings-->
   <input name="ap:settings/ssid0/privacy_type" value="2" id="uiPostPrivacyType" type="hidden">
   <input name="ap:settings/ssid0/wep_privacy" value="1" id="uiPostWepEnabled" type="hidden">
   <input name="ap:settings/ssid0/wep_auth_type" value="1" id="uiPostAuthType" type="hidden">
   <input name="ap:settings/ssid0/key_id" value="0" id="uiPostKeyId" type="hidden">
   <input name="ap:settings/ssid0/key_value1" value="FF******7F" id="uiPostKeyValue1" type="hidden">
   <input name="ap:settings/ssid0/key_len1" value="5" id="uiPostKeyLen1" type="hidden">
   <input name="ap:settings/ssid0/key_value2" value="" id="uiPostKeyValue2" type="hidden">
   <input name="ap:settings/ssid0/key_len2" value="5" id="uiPostKeyLen2" type="hidden">
   <input name="ap:settings/ssid0/key_value3" value="" id="uiPostKeyValue3" type="hidden">
   <input name="ap:settings/ssid0/key_len3" value="5" id="uiPostKeyLen3" type="hidden">
   <input name="ap:settings/ssid0/key_value4" value="" id="uiPostKeyValue4" type="hidden">
   <input name="ap:settings/ssid0/key_len4" value="5" id="uiPostKeyLen4" type="hidden">
</form>

<script type="text/javascript">
	inTableEnd();
	mainTableEnd();
</script></td><td width="19" background="dlinkwirelesswebcm_files/right2.gif" height="100%"><img src="dlinkwirelesswebcm_files/sp.gif" heigh="10" width="19"></td><td width="25" background="dlinkwirelesswebcm_files/right1.gif" height="100%"><img src="dlinkwirelesswebcm_files/sp.gif" heigh="10" width="25"></td></tr><tr><td width="100%" background="dlinkwirelesswebcm_files/last1.jpg" height="44">&nbsp;</td><td width="100%" background="dlinkwirelesswebcm_files/last2.jpg" height="44">&nbsp;</td><td colspan="2" width="100%" background="dlinkwirelesswebcm_files/last3.jpg" height="44">&nbsp;</td><td colspan="2" width="25" background="dlinkwirelesswebcm_files/last4.jpg" height="44">&nbsp;</td></tr></tbody></table>
</body></html>
[/HTML]

---

### Post by Ryuhayabusa on 2009-04-11
I'm probably being annoying now.

I've got the cable out, disabled WEP and connected using the atheros pcmcia card

```

lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"jacqio"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:22:B0:94:29:B6   
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:8   Missed beacon:3

```

```

ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe02:5d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:357 errors:32738 dropped:0 overruns:0 frame:32738
          TX packets:314 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:392004 (382.8 KB)  TX bytes:28644 (27.9 KB)
          Interrupt:11 Memory:d8300000-d8310000 

eth0      Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          inet6 addr: fe80::200:e2ff:fe8c:71e5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3938145 (3.7 MB)  TX bytes:913019 (891.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9646 (9.4 KB)  TX bytes:9646 (9.4 KB)

```

the lights on my card labelled act and link are flashing at the same time. Which is different to when it's not working. When that happens they do it one at a time.

---

### Post by chili555 on 2009-04-11
> i'll try to find out why i've got 2 jacqio's. Often they have slightly different Signal level'sAre you running iwlist as sudo? If not, it only provides left-over results. This is from *man iwlist*:> Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.I see 'iwlist scan' on this forum continually and complaints about the goofy result.> ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe02:5d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:357 errors:32738 dropped:0 overruns:0 frame:32738
          TX packets:314 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          [COLOR="Red"]RX bytes:392004 (382.8 KB)  TX bytes:28644 (27.9 KB)[/COLOR]Looks to me like you are connected! Are we golden?

---

### Post by Ryuhayabusa on 2009-04-11
chilli
i can connect but only when i disable WEP on my router. The router has three wep settings: open, shared and both. I am using shared because that is what is working with my fathers vista laptop (and i'm hopeless at getting things to work).

---

### Post by chili555 on 2009-04-11
I suggest you edit the */etc/network/interfaces* file to change the ath0 stanza to:```
#auto ath0 
iface ath0 inet static
address 192.168.1.49
gateway 192.168.1.254
netmask 255.255.255.0
wireless-key FF******7F [COLOR="Red"]restricted[/COLOR]
wireless-essid jacqio
wpa-driver wext
```Leave all the other parts unchanged. After you put WEP back in place in the router, please try:```
sudo ifdown ath0 && sudo ifup ath0
```Please let us know if you connect or notice any errors. 

I am suspicious of this:> wpa-driver wextI thought WPA drivers were for WPA and not WEP. Did the Ubuntu Guide tell you to add that? If you do not connect after making the changes above, comment out that line, thus:```
#auto ath0 
iface ath0 inet static
address 192.168.1.49
gateway 192.168.1.254
netmask 255.255.255.0
wireless-key FF******7F restricted
wireless-essid jacqio
#wpa-driver wext
```See if you connect.

---

### Post by Ryuhayabusa on 2009-04-11
> **chili555 said:**
> I suggest you edit the */etc/network/interfaces* file to change the ath0 stanza to:```
#auto ath0 
iface ath0 inet static
address 192.168.1.49
gateway 192.168.1.254
netmask 255.255.255.0
wireless-key FF******7F [COLOR="Red"]restricted[/COLOR]
wireless-essid jacqio
wpa-driver wext
```Leave all the other parts unchanged. After you put WEP back in place in the router, please try:```
sudo ifdown ath0 && sudo ifup ath0
```


[COLOR="Blue"]
these are the messages
```

sudo ifdown ath0 && sudo ifup ath0 
ifdown: interface ath0 not configured
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
sunil@gman:~$  * Stopping NTP server ntpd
   ...done.sudo ifdown ath0 && sudo ifup ath0 
ifdown: interface ath0 not configured
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
sunil@gman:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

 * Starting NTP server ntpd
   ...done.

```[/COLOR]

> 
Please let us know if you connect or notice any errors. 

I am suspicious of this:I thought WPA drivers were for WPA and not WEP. Did the Ubuntu Guide tell you to add that? If you do not connect after making the changes above, comment out that line, thus:```
#auto ath0 
iface ath0 inet static
address 192.168.1.49
gateway 192.168.1.254
netmask 255.255.255.0
wireless-key FF******7F restricted
wireless-essid jacqio
#wpa-driver wext
```See if you connect.

[COLOR="blue"]I did put that in because i plan to use the card with WPA later on at school. I'm using wicd at the moment. Is that a problem maybe?[/COLOR]

---

### Post by chili555 on 2009-04-11
> I did put that in because i plan to use the card with WPA later on at school. I'm using wicd at the moment. Is that a problem maybe?> ioctl[SIOCSIWENCODEEXT]: Operation not supportedYes, I think it is and so does, evidently, your computer. Does it connect correctly when you comment the wext line out?

---

### Post by Ryuhayabusa on 2009-04-11
the wext line is commented out now.

I have reactivated WEP with the setting on 'both' shared and open keys.

this is what i tried 

```

sunil@gman:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet6 addr: fe80::217:9aff:fe02:5d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5260 errors:5239 dropped:0 overruns:0 frame:5239
          TX packets:5278 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:4581745 (4.3 MB)  TX bytes:829562 (810.1 KB)
          Interrupt:11 Memory:d82e0000-d82f0000 

eth0      Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          inet6 addr: fe80::200:e2ff:fe8c:71e5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1636659 (1.5 MB)  TX bytes:376521 (367.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11992 (11.7 KB)  TX bytes:11992 (11.7 KB)

sunil@gman:~$ sudo iwlist ath0 scan
[sudo] password for sunil: 
ath0      Scan completed :
          Cell 01 - Address: 00:22:B0:94:29:B6
                    ESSID:"jacqio"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200

sunil@gman:~$ iwconfig 
sunil@gman:~$ sudo iwconfig ath0 essid "jacqio" key ff7aa7b47f
sunil@gman:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"jacqio"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:22:B0:94:29:B6   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:4   Missed beacon:3

sit0      no wireless extensions.

sunil@gman:~$ ping router
connect: Network is unreachable
sunil@gman:~$ sudo ifdown ath0 && sudo ifup ath0 
ifdown: interface ath0 not configured
 * Stopping NTP server ntpd
   ...done.
sunil@gman:~$  * Starting NTP server ntpd
   ...done.
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"jacqio"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:22:B0:94:29:B6   
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/94  Signal level=-75 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:4   Missed beacon:3

sit0      no wireless extensions.

sunil@gman:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:17:9a:02:5d:9e  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe02:5d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5269 errors:5497 dropped:0 overruns:0 frame:5497
          TX packets:5296 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:4582683 (4.3 MB)  TX bytes:831944 (812.4 KB)
          Interrupt:11 Memory:d82e0000-d82f0000 

eth0      Link encap:Ethernet  HWaddr 00:00:e2:8c:71:e5  
          inet6 addr: fe80::200:e2ff:fe8c:71e5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1636659 (1.5 MB)  TX bytes:376521 (367.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11992 (11.7 KB)  TX bytes:11992 (11.7 KB)


```

---

### Post by Ryuhayabusa on 2009-04-11
my god i'm embarrased.

the problem is resolved.

in wicd i set the ip address for the wireless to the SAME as the ethernet.

This was way before i came to the forum for help. I don't really understand IP addresses. I now have a connection which is working flawlessly.

I can't thank chili enough for the help. I learnt alot from the experience.

My brother says that when i do computing i don't think enough about the processes just keep trying things over and over again.

I think it partially because when you come from windows you just learn which ones to click to get it to work. And when you come to the forums, sometimes the solution is just posted for you without people like me gaining an understanding of what the stuff actually is. I think that I will have to look at some Wiki's.

---

