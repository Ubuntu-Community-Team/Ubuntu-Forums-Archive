---
title: "Firewall Builder"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by paulZachJones on 2013-03-28
After working with Proxmox recently, I have been interested in a different way to make firewalls. After struggling with ufw, I stuck to iptables directly. After much practice, I have built a webapp using PHP, Javascript, and html for creating a linux script to run and properly filter and log. It is merely in the alpha stages but I'd would appreciate any help with it. It currently only supports tcp(apart from udp for dns, and icmp for pings.) It assumes that you have an iptables chain called LOGGING(iptables -N LOGGING), that your default policies are to DROP, and that you would like internet and dns access for the host and it's "guests." A guest is a virtual machine in proxmox, or other virtual machine host, you type in all of their predefined IP address and the services, including client services.
This program also works quite well with only a normal computer setup. If you are using client services, you must define them(ssh, ftp, etc.)

```

<!DOCTYPE html>
<html>
<head>
<script>
  function show()
  {
    var mach = ["host","first","second","third","fourth","fifth","sixth","seventh","eighth","ninth","tenth"];
    var serv = ["First","Second","Third","Fourth","Fifth","Sixth","Seventh","Eighth","Ninth","Tenth"];
    for(var i = 0; i < 11; i++)
    {
      for(var j = 0; j < 9; j++)
      {
        if(document.getElementById(mach[i]+serv[j]+"Name").value != "")
          document.getElementById(mach[i]+serv[j+1]+"ServiceDiv").style.display='inline';
        else
          document.getElementById(mach[i]+serv[j+1]+"ServiceDiv").style.display='none';
      }
    }


    for(var i = 1; i < 10; i++)
    {
        if(document.getElementById(mach[i]+"Nickname").value != "Nickname")
          document.getElementById(mach[i+1]+"Div").style.display='block';
        else
          document.getElementById(mach[i+1]+"Div").style.display='none';
    }
  }


function build()
{
  document.getElementById("buildDisplay").innerHTML="iptables -F\n";
  var white = new Array();
  var whiteCount = 0;
  if(document.getElementById("firstWhitelist").value!="") white[whiteCount++] = document.getElementById("firstWhitelist").value;
  if(document.getElementById("secondWhitelist").value!="") white[whiteCount++] = document.getElementById("secondWhitelist").value;
  if(document.getElementById("thirdWhitelist").value!="") white[whiteCount++] = document.getElementById("thirdWhitelist").value;
  if(document.getElementById("fourthWhitelist").value!="") white[whiteCount++] = document.getElementById("fourthWhitelist").value;
  if(document.getElementById("fifthWhitelist").value!="") white[whiteCount++] = document.getElementById("fifthWhitelist").value;
  if(document.getElementById("sixthWhitelist").value!="") white[whiteCount++] = document.getElementById("sixthWhitelist").value;
  if(document.getElementById("seventhWhitelist").value!="") white[whiteCount++] = document.getElementById("seventhWhitelist").value;
  if(document.getElementById("eighthWhitelist").value!="") white[whiteCount++] = document.getElementById("eighthWhitelist").value;
  //host
  document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p udp --sport 53 -j ACCEPT\niptables -A OUTPUT -p udp --dport 53 -j ACCEPT\niptables -A INPUT -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT\niptables -A OUTPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT\niptables -A OUTPUT -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT\niptables -A INPUT -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT\n";


  if(document.getElementById("hostICMP").checked)
    document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT\niptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT\niptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT\niptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT\n";
<?php
$services=array("First","Second","Third","Fourth","Fifth","Sixth","Seventh","Eighth","Ninth","Tenth");
$guests=  array("first","second","third","fourth","fifth","sixth","seventh","eighth","ninth","tenth");
foreach($services as &$i)
{
echo '
  if(document.getElementById("host'.$i.'Name").value!="")
  {
    var dPort, sPort, list, listCount, inp, out;
    if(document.getElementById("host'.$i.'Server").checked)
    {
      dPort=document.getElementById("host'.$i.'Port").value;
      sPort="1024:65535";
    }
    else
    {
      sPort=document.getElementById("host'.$i.'Port").value;
      dPort="1024:65535";
    }
    if(document.getElementById("host'.$i.'Whitelist").checked)
    {
      list=white;
      listCount=whiteCount;
    }
    else
    {
      list=new Array();
      list[0]="0.0.0.0/0";
      listCount=1;
    }
    for(var i = 0; i < listCount; i++)
    {
      document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+" -m state --state ESTABLISHED -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A OUTPUT -p tcp --sport "+dPort+" --dport "+sPort+" -d "+list[i]+" -m state --state ESTABLISHED,NEW -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp --dport "+dPort+" --sport "+sPort+" -m state --state NEW -m limit --limit "+document.getElementById("host'.$i.'Limit").value+"/min --limit-burst "+document.getElementById("host'.$i.'Limit").value*2+" -s "+list[i]+" -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp --dport "+dPort+" --sport "+sPort+" -m state --state NEW -m limit -s "+list[i]+" -j LOGGING\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A LOGGING -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+\' -j LOG --log-prefix "Host \'+document.getElementById("host'.$i.'Name").value+\' has had too many new connections!!!"\n\';
      document.getElementById("buildDisplay").innerHTML+="iptables -A LOGGING -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+\' -j DROP\n\';




      
    }
  }'; 
  }
foreach($guests as &$z)
{
echo 'if(document.getElementById("'.$z.'Nickname").value!="Nickname")
{
  document.getElementById("buildDisplay").innerHTML+="iptables -A FORWARD -p udp --sport 53 --dport 1024:65535 -d "+document.getElementById(\''.$z.'IP\').value+" -j ACCEPT\niptables -A FORWARD -s "+document.getElementById(\''.$z.'IP\').value+" -j ACCEPT\niptables -A FORWARD -p tcp --sport 80 -d "+document.getElementById(\''.$z.'IP\').value+" -m state --state ESTABLISHED -j ACCEPT\niptables -A FORWARD -p tcp --sport 443 -d "+document.getElementById(\''.$z.'IP\').value+" -m state --state ESTABLISHED -j ACCEPT\n";


    document.getElementById("buildDisplay").innerHTML+="iptables -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT\niptables -A FORWARD -p icmp --icmp-type echo-reply -j ACCEPT\n";
';


foreach($services as &$i)
{
echo '
  if(document.getElementById("'.$z.$i.'Name").value!="")
  {
    var dPort, sPort, list, listCount, inp, out;
    if(document.getElementById("'.$z.$i.'Server").checked)
    {
      dPort=document.getElementById("'.$z.$i.'Port").value;
      sPort="1024:65535";
    }
    else
    {
      sPort=document.getElementById("'.$z.$i.'Port").value;
      dPort="1024:65535";
    }
    if(document.getElementById("'.$z.$i.'Whitelist").checked)
    {
      list=white;
      listCount=whiteCount;
    }
    else
    {
      list=new Array();
      list[0]="0.0.0.0/0";
      listCount=1;
    }
    for(var i = 0; i < listCount; i++)
    {
      document.getElementById("buildDisplay").innerHTML+="iptables -A FORWARD -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+" -d "+document.getElementById(\''.$z.'IP\').value+" -m state --state ESTABLISHED -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A FORWARD -p tcp --dport "+dPort+" --sport "+sPort+" -d "+document.getElementById(\''.$z.'IP\').value+" -m state --state NEW -m limit --limit "+document.getElementById("host'.$i.'Limit").value+"/min --limit-burst "+document.getElementById("host'.$i.'Limit").value*2+" -s "+list[i]+" -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A FORWARD -p tcp --dport "+dPort+" --sport "+sPort+" -d "+document.getElementById(\''.$z.'IP\').value+" -m state --state NEW -m limit -s "+list[i]+" -j LOGGING\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A LOGGING -p tcp --dport "+dPort+" --sport "+sPort+" -d "+document.getElementById(\''.$z.'IP\').value+" -s "+list[i]+\' -j LOG --log-prefix "Guest \'+document.getElementById("'.$z.'Nickname").value+"\'s "+document.getElementById("'.$z.$i.'Name").value+\' has had too many new connections!!"\n\';
      document.getElementById("buildDisplay").innerHTML+="iptables -A LOGGING -p tcp --dport "+dPort+" --sport "+sPort+" -d "+document.getElementById(\''.$z.'IP\').value+" -s "+list[i]+\' -j DROP\n\';




    } //end forloop
  } //end if service active
';} //end foreach service
echo '}'; //end if this guest active
} //end foreach guest
?> 


};
</script>
</head>
<body onload="show()">
<form>
<input type="button" id="submitButton" value="Build" onClick="build()">
<div style="border: 1px solid grey; overflow: hidden">
<div style="float: left"><pre>WHITELIST
<?php
//$guests=  array("first","second","third","fourth","fifth","sixth","seventh","eighth","ninth","tenth");
foreach ($guests as $i)
{
  echo '
<input type="text" id="'.$i.'Whitelist">';
}
echo "
";
?>
</div>
<textarea id="buildDisplay" style="float: left"></textarea>
</div>
<pre>


<div style="overflow: hidden; border: 1px solid black">
Host's IP Address <input type="text" id="hostIP">
Allow ICMP?<input type="checkbox" id="hostICMP" value="yes">


<?php
$services=array("First","Second","Third","Fourth","Fifth","Sixth","Seventh","Eighth","Ninth","Tenth");
//$guests=  array("first","second","third","fourth","fifth","sixth","seventh","eighth","ninth","tenth");
foreach ($services as &$i){
echo '<div id="host'.$i.'ServiceDiv" style="float: left; border: 1px solid red;">'.$i.' Service
 Name    <input onchange="show()" type="text" id="host'.$i.'Name">
 Port    <input type="text" id="host'.$i.'Port">
 Limit   <input type="text" id="host'.$i.'Limit">
 Server?   <input type="checkbox" id="host'.$i.'Server" value="yes">
 Whitelist?<input type="checkbox" id="host'.$i.'Whitelist" value="yes"></div>';
}
echo '</pre></div>';






foreach ($guests as &$i){
echo "<br>";
echo '<pre><div id="'.$i.'Div" style="overflow: hidden; border: 1px solid green"><b>'.$i.' guest</b>


<input onchange="show()" type="text" id="'.$i.'Nickname" value="Nickname">
Guest IP Address<input type="text" id="'.$i.'IP">


';


foreach ($services as &$j){
echo '<div id="'.$i.$j.'ServiceDiv" style="float: left; border: 1px solid red">'.$j.' Service
 Name    <input onchange="show()" type="text" id="'.$i.$j.'Name">
 Port    <input type="text" id="'.$i.$j.'Port">
 Limit   <input type="text" id="'.$i.$j.'Limit">
 Server?   <input type="checkbox" id="'.$i.$j.'Server" value="yes">
 Whitelist?<input type="checkbox" id="'.$i.$j.'Whitelist" value="yes"></div>';
}


echo '</form></pre></div>';}
?>


<br>
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/deed.en_US"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">Iptables Script Builder</span> by <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">Michael Smith</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/deed.en_US">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License</a>.
</body>
</html>

```

---

### Post by paulZachJones on 2013-04-09
Or a simplified version for all computers
```

<!DOCTYPE html>
<html>
<head>
<script>
function build()
{
  document.getElementById("buildDisplay").innerHTML="iptables -F\n";
  var white = new Array();
  var whiteCount = 0;
  if(document.getElementById("firstWhitelist").value!="") white[whiteCount++] = document.getElementById("firstWhitelist").value;
  if(document.getElementById("secondWhitelist").value!="") white[whiteCount++] = document.getElementById("secondWhitelist").value;
  if(document.getElementById("thirdWhitelist").value!="") white[whiteCount++] = document.getElementById("thirdWhitelist").value;
  if(document.getElementById("fourthWhitelist").value!="") white[whiteCount++] = document.getElementById("fourthWhitelist").value;
  if(document.getElementById("fifthWhitelist").value!="") white[whiteCount++] = document.getElementById("fifthWhitelist").value;
  if(document.getElementById("sixthWhitelist").value!="") white[whiteCount++] = document.getElementById("sixthWhitelist").value;
  if(document.getElementById("seventhWhitelist").value!="") white[whiteCount++] = document.getElementById("seventhWhitelist").value;
  if(document.getElementById("eighthWhitelist").value!="") white[whiteCount++] = document.getElementById("eighthWhitelist").value;
  document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p udp --sport 53 -j ACCEPT\niptables -A OUTPUT -p udp --dport 53 -j ACCEPT\niptables -A INPUT -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT\niptables -A OUTPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT\niptables -A OUTPUT -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT\niptables -A INPUT -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT\n";


  if(document.getElementById("hostICMP").checked)
    document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT\niptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT\niptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT\niptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT\n";
<?php
$services=array("First","Second","Third","Fourth","Fifth","Sixth","Seventh","Eighth","Ninth","Tenth");
$guests=  array("first","second","third","fourth","fifth","sixth","seventh","eighth","ninth","tenth");
foreach($services as &$i)
{
echo '
  if(document.getElementById("host'.$i.'Name").value!="")
  {
    var dPort, sPort, list, listCount, inp, out;
    if(document.getElementById("host'.$i.'Server").checked)
    {
      dPort=document.getElementById("host'.$i.'Port").value;
      sPort="1024:65535";
    }
    else
    {
      sPort=document.getElementById("host'.$i.'Port").value;
      dPort="1024:65535";
    }
    if(document.getElementById("host'.$i.'Whitelist").checked)
    {
      list=white;
      listCount=whiteCount;
    }
    else
    {
      list=new Array();
      list[0]="0.0.0.0/0";
      listCount=1;
    }
    for(var i = 0; i < listCount; i++)
    {
      document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+" -m state --state ESTABLISHED -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A OUTPUT -p tcp --sport "+dPort+" --dport "+sPort+" -d "+list[i]+" -m state --state ESTABLISHED,NEW -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp --dport "+dPort+" --sport "+sPort+" -m state --state NEW -m limit --limit "+document.getElementById("host'.$i.'Limit").value+"/min --limit-burst "+document.getElementById("host'.$i.'Limit").value*2+" -s "+list[i]+" -j ACCEPT\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp --dport "+dPort+" --sport "+sPort+" -m state --state NEW -m limit -s "+list[i]+" -j LOGGING\n";
      document.getElementById("buildDisplay").innerHTML+="iptables -A LOGGING -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+\' -j LOG --log-prefix "Host \'+document.getElementById("host'.$i.'Name").value+\' HIT LIMIT"\n\';
      document.getElementById("buildDisplay").innerHTML+="iptables -A LOGGING -p tcp --dport "+dPort+" --sport "+sPort+" -s "+list[i]+\' -j DROP\n\';
    }
  }'; 
  }
?> 
document.getElementById("buildDisplay").innerHTML+="iptables -A INPUT -p tcp -j REJECT --reject-with tcp-reset\niptables -A INPUT -p icmp -j REJECT\niptables -A INPUT -j DROP\niptables -A OUTPUT -j DROP\n";
};
</script>
</head>
<body>
<form>
<input type="button" id="submitButton" value="Build" onClick="build()">
<pre>WHITELIST
<?php
//$guests=  array("first","second","third","fourth","fifth","sixth","seventh","eighth","ninth","tenth");
foreach ($guests as $i)
{
  echo '
<input type="text" id="'.$i.'Whitelist">';
}
echo "
";
?>
<textarea id="buildDisplay" style="float: left"></textarea>
<br>
<pre>
Allow ICMP?<input type="checkbox" id="hostICMP" value="yes">


<?php
$services=array("First","Second","Third","Fourth","Fifth","Sixth","Seventh","Eighth","Ninth","Tenth");
foreach ($services as &$i){
echo $i.' Service
 Name    <input onchange="show()" type="text" id="host'.$i.'Name">
 Port    <input type="text" id="host'.$i.'Port">
 Limit   <input type="text" id="host'.$i.'Limit">
 Server?   <input type="checkbox" id="host'.$i.'Server" value="yes">
 Whitelist?<input type="checkbox" id="host'.$i.'Whitelist" value="yes">';
}
echo '</pre>';
?>

```

---

