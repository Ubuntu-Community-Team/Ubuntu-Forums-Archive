---
title: "GratisDNS.dk DynamicIP updater bash script"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by HavarN on 2012-02-21
I tried posting this to the [GratisDNS.dk]("http://gratisdns.dk") forum. However, it seems new users can't post new threads over there. And it is probably only relevant for *nix users. I will post it here in case it can help anyone looking for this script for *nix.

Copy this into a file on your computer and make it executable:```
#!/bin/bash

writeusage () {
	echo "Usage:"
	echo
	echo $'\t'$0 "-u username -p password -h host -d domain"
	echo
	echo $'\t'All arguments are needed.
	echo
}
showargs () {
  for p in "$@"
    do
      echo "$p"
    done
}
# Thanks to Mitch Frazier @ http://www.linuxjournal.com/content/validating-ip-address-bash-script
function valid_ip()
{
    local  ip=$1
    local  stat=1

    if [[ $ip =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$ ]]; then
        OIFS=$IFS
        IFS='.'
        ip=($ip)
        IFS=$OIFS
        [[ ${ip[0]} -le 255 && ${ip[1]} -le 255 \
            && ${ip[2]} -le 255 && ${ip[3]} -le 255 ]]
        stat=$?
    fi
    return $stat
}

cont=true
# Get the external ip from http://www.XplainASP.dk/public/myip.asp
ip=$(wget -q http://www.XplainASP.dk/public/myip.asp -O -)
while getopts "p:u:h:d:" optname
    do
      case "$optname" in
        "p")
          password=$OPTARG
          ;;
        "u")
	  username=$OPTARG
          ;;
        "h")
	  host=$OPTARG
          ;;
        "d")
	  domain=$OPTARG
          ;;
        "?")
          cont=false
          ;;
        ":")
          cont=false
          ;;
        *)
        # Should not occur
          echo "Unknown error while processing options"
          ;;
      esac
    done

argstart=$OPTIND
arginfo=$(showargs "${@:$argstart}")

# Check for missing arguments
if [ "$username" = "" ] && [ "$password" = "" ] && [ "$host" = "" ] && [ "$domain" = "" ]; then cont=false; fi
if [ $cont = false ]; then
	echo $'\n'Missing arguments.
	writeusage
	exit
fi

# Check for invalid arguments
if [ "$arginfo" != "" ]; then
	echo $'\n'"Invalid arguments: $arginfo"
	echo
	writeusage
	echo
 	echo However all required arguments are given, so I will try to continue.
fi

PING=$(ping -c 1 -w 3 $ip | grep time= | sed 's/\(^.*time=\)\(.*\)\(ms.*$\)/\2/')" ms"
response=$(if [ "$PING" != " ms" ]; then echo "responding after "$PING; else echo "unresponsive"; fi )
validip=$(if valid_ip $ip; then echo "valid"; else echo "invalid"; fi)

echo
echo Your external IP $ip is $validip and $response
if [ "$PING" = " ms" ]; then
	echo Will not try to update $host @ $domain
	echo
	exit
fi
echo

updateurl=$(echo "https://ssl.gratisdns.dk/ddns.phtml?u="$(echo $username | sed 's/ /%20/')"&p="$(echo $password | sed 's/ /%20/')"&d="$domain"&h="$host"&i="$ip)
response=$(wget -q $updateurl -O - | sed -e "s/<.*[bB][rR]>/\n/" | sed -e "s/<.*>//" | sed -e "s/Opdateret i forvejen/Already updated/" )
echo Response from gratisdns.dk:
echo $'\t'$response
echo
```

---

