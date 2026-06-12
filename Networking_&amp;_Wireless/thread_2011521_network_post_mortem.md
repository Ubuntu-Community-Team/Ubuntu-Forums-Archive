---
title: "network post mortem"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by mringer on 2012-06-27
We see many threads that start:

Mourner: My network is dead.
Expert: Please publish the results of (a list of commands).

Sometimes mistakes are made and it takes 2 or 3 rounds before the Expert can say what is wrong. About a year ago a program was posted by Hippytaff:

[http://ubuntuforums.org/showthread.php?t=1706952](http://ubuntuforums.org/showthread.php?t=1706952)

which is a shell script that runs these diagnostic commands. I believe that this type of program could be extremely valuable and that the author deserves far more credit than people seem to have given him/her. It seems as if nobody realised how desperately this type of program is needed. 
I have written my version:


```

#!/bin/bash

# ***************************   Set up files

filter=1
bin=/dev/null
outfile="test"

while [ $# -gt 0 ] ; do
    if [ $1 = "-f" ] && [ $# -eq 1 ] ; then
	    echo "error: -f with no filename "
	    exit 1
    elif [ $1 = "-f" ] ; then
	outfile=$2 ; shift ; shift
    elif [ $1 = "-n" ] ; then
	filter=0 ; shift
    else
	echo "error: illegal option $1"
	echo "usage:  sudo net-test [-n] [-f file] "
	exit 1
    fi
done

tmpfile=$outfile.tmp
logfile=$outfile.log


echo >$tmpfile '******** net test ******* ' 
if test $? -ne 0
then
    echo "Error: cannot write $tmpfile"
    exit 1
fi

cp $tmpfile $logfile
if test $? -eq 0
then
    echo "Output on file $logfile"
else
    echo "Error: cannot write $logfile"
    exit 1
fi

date >>$logfile 
uname -a >> $logfile
lsb_release -d >>$logfile


# ***************************   Functions

do_command() {
    echo $1
    echo -e "\n\n ******** $* ******* \n" > $tmpfile
    $* >> $tmpfile
    cat $tmpfile >>$logfile
}


# Run a command and filter the output. Usage:
#         do_filter command arguments grep patterns
# Run the command then filter the output for patterns

do_filter() {
    echo $1
    cmd=$( 
	while test $1 != "grep" ; do
	    echo -n " $1 " ; shift;
	done)
    if [ $filter -eq 1 ] ; then
	echo -e "\n\n ******** $cmd (filtered) ******* \n" >> $logfile
	list=$( 
	    while test $1 != "grep" ; do
		shift ;
	    done
	    shift
	    while test "$1" != "" ; do
		echo -e "-e $1" ; shift;
	    done )
	$cmd | grep -i $list >$tmpfile 
	cat $tmpfile >>$logfile
    else
	do_command $cmd
    fi
}


# ***************************  lshw  *************************** 


do_command lshw -C net

<$logfile grep -A1 -e network -e name -e configuration |
    tr -s ' '     |
    tr ' ' '\n '  |
    grep -A1 -e network  -e description -e name -e 'driver=' |
    grep -v -e -- -e driverversion |
    tr '\n' ' ' |
    tr '*' '\n' >$tmpfile 

duds=$( <test.tmp grep UNCLAIMED | 
    sed "s/.*name: \([^ ]*\).*/\1/g" |
    tr '\n' ' ' )

if test "$duds" != ""  ; then
    echo "Fault: lshw: UNCLAIMED devices: $duds"
fi

ethers=$( <test.tmp grep -v UNCLAIMED |
    grep -ie ethernet |
    sed "s/.*name: \([^ ]*\).*/\1/g"  |
    tr '\n' ' ' )
echo "Ethernets: $ethers"

radios=$( <test.tmp grep -v UNCLAIMED |
    grep -ie wireless |
    sed "s/.*name: \([^ ]*\).*/\1/g"  |
    tr '\n' ' ' )
echo "Wireless: $radios"

drivrs=$( 
<$tmpfile grep -e 'driver=' |
    cut -d= -f2 |
    tr + '\n'   |
    tr -d ' '   |
    sort | uniq |
    tr '\n' ' ' 
)
echo "drivers: $drivrs"



# *************************** other diagnostics ************************** 


do_command rfkill list all
if grep yes $tmpfile > $bin 2>$bin ; then
    echo "Fault: rfkill: A device is blocked"
fi


do_filter lspci grep net

nets=$( grep -ie net $tmpfile |
    tr [:blank:] + |
    cut -d+ -f1 )

echo -e "\n\n DETAILS " >>$logfile
for i in $nets; do
    echo -e "\n" >>$logfile
    lspci -v -s$i >>$logfile
done


do_filter dmesg grep $drivrs $names net tcp


do_command lsmod


do_command lsusb


do_filter ps ax grep wicd networkman
if grep -i wicd $tmpfile > $bin &&
    grep -i networkmanager $tmpfile >$bin ; then
    echo "Fault: ps: running both wicd and network manager"
fi


do_command ifconfig

for i in $ethers ; do
    ifconfig $i up
done

for i in $radios ; do
    ifconfig $i up
    do_command iwconfig $i
    do_filter iwlist $i scan grep scan cell essid quality encrypt
done


chmod 777 $tmpfile $logfile
exit 0


```

I realise that this offers a lot of scope for improvement. In particular, there is no adequate document. If users like the program, I will try to write a Texinfo file. Meanwhile here is a man page:

```

.\"
.TH NET-TEST "1" "June 2012" "net-test "
.SH NAME
net-test \- test local network
.SH SYNOPSIS
.B [sudo] net-test
[\fIoptions\fR]
.SH DESCRIPTION
Run tests on local network interfaces.
It is hoped that an expert will be able to
read the output and say why your
network is not working. Net-test also has a very limited ability
to diagnose some faults.
By default, net-test sends its output to \fBtest.log\fR
in the current working directory. It also uses a
temporary file \fBtest.tmp\fR  It is an error if
these files cannot be written. Program will run
without sudo but the diagnostics will be less useful.

.SH OPTIONS
.TP
\fB\-n\fR
By default the output is filtered to delete lines
thought to be irrelevant. \fB\-n\fR gives you the
output in full.
.TP
\fB\-f FILE\fR
This  changes the output files to \fBFILE.log\fR and
\fBFILE.tmp\fR .

.SH "RETURNS"
Net-test returns 0 on success, 1 on error.
.SH "SEE ALSO"
The full document for this program does not yet
exist. It is hoped that it will appear
as a Texinfo manual.


```

---

### Post by chili555 on 2012-06-27
I suggest a change or two. Instead of lspci grep net, I suggest you lspci -nn grep -e 0200 -e 0280. Not every wireless card has the word Network in its name. Second, the pci.id or usb.id is the most valuable piece of data there is. Please capture and display it.

I am continuing to study the results and expect to make more comments later.

The results are quite lengthy. Do you suggest posters put all the data in a long forum post or pastebin or what?

---

### Post by chili555 on 2012-06-27
You might look at mintWifi here: [http://packages.linuxmint.com/pool/main/m/mintwifi/](http://packages.linuxmint.com/pool/main/m/mintwifi/) It does a similar job.

---

### Post by mringer on 2012-06-29
I have noted replies from chili555 . Also I found a bug: net-test
sometimes reports falsely that you are running both wicd & Network
Manager. To be fixed soon I hope.

---

