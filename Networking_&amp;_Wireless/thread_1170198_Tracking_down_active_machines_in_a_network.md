---
title: "Tracking down active machines in a network"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by codingfreak on 2009-05-26
Hi

How can I find the IP-Adresses of all active machines [Powered ON] in a Network ??

Is there any other way without using the tools like nmap ??

---

### Post by chili555 on 2009-05-26
I think nmap is the best tool:```
nmap -sP 192.168.1.*
```Substitute your IP range here. Why do you not want to use nmap?

---

### Post by codingfreak on 2009-05-27
> **chili555 said:**
> I think nmap is the best tool:```
nmap -sP 192.168.1.*
```Substitute your IP range here. Why do you not want to use nmap?

Thanks for the reply chili .....

Actually the reason I dont want to use nmap is to write my own application in C to find out how can I simulate the whole process.

Can you get me even the nmap command to get information about the type of OS being used on that machine.

---

### Post by chili555 on 2009-05-27
> Can you get me even the nmap command to get information about the type of OS being used on that machine.Reading The Friendly Manual suggests it is:```
sudo nmap -O 192.168.1.*
```

---

### Post by irv on 2009-05-27
> **chili555 said:**
> Reading The Friendly Manual suggests it is:```
sudo nmap -O 192.168.1.*
```

I like using the GUI for nmap which is nmapsi4 and nmapsi4-Root mode.

---

### Post by lavinog on 2009-05-27
I have found it helps to use the -n switch to prevent dns queries on local computers

---

### Post by codingfreak on 2009-05-29
So any help regarding programming an application that can do the same thing ???

---

### Post by lavinog on 2009-05-29
I finished making a bash script yesterday to get mac addresses for all active machines.
It can use nmap, but I made a function to handle getting ip addresses using ping instead.
[http://ubuntuforums.org/showthread.php?t=1172591](http://ubuntuforums.org/showthread.php?t=1172591)
```

pingit()
{
ping -n -c 1 -W 1 ${1}>/dev/null && echo ${1}>>${tmpfile}
}

pingall()
{
# ping all addresses in block
# (much slower than nmap)

ip_prefix=$(echo ${self_ip_addr}|cut -d '.' -f 1-3)

for i in {1..254}
do
    # Ip address to ping
    ip="${ip_prefix}.${i}"

    # ping in background
    pingit ${ip}&
    
    # Wait for all ping blocks to finish
    [[ $(( ${i}%${ipblocks} )) -eq 0 ]]&&{
    echo -n '|'
    wait
    }
done

# wait for last batch of pings
wait

# remove progress line
echo -en '\r'



} 
```
basically, it executes a ping command in the background. ipblocks = 51 and keeps the number of outstanding packets under 51.
it saves the results into a temporary file for further use.

---

### Post by jonobr on 2009-05-29
You could also try using a program like SNMP walk

SNMP is enabled on a lot devices out there by default and you can query things like OS, as well as a lot of other info.

SNMPwalk is found in Synaptic in the package SNMP in universe.

Querying the remote device via command line uses
snmpwalk -c <string> <target> <oid>

where -c <string> = community string (for level of access , usually public *read only and private *read/write) the defaults are usually rearely changed.

target = remote IP address or hostname
<OID> object ID= string of nubmers representing a id, such as OS name, and many other pieces of info.

SNMP can also be used with the like of perl ( as a module to Perl)  so it can be used in programming

---

### Post by Adina on 2009-05-29
maybe not what you are looking for, but have you tried iptraf?

It looks in a way similar to wireshark, but don't monitor packets. only ip traffic on a lan.

---

### Post by puppywhacker on 2009-05-29
And as a simple solution, just list the nodes that you are talking to which are part of the arp list. the ones you learned the ip-address from, by talking straight to them.

```
arp -a
```

---

