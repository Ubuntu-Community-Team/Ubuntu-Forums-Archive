---
title: "Campus wifi"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by EMR on 2011-02-22
I've had some trouble getting onto my campus's LAN with my xubuntu machine.  It won't let me on unless I install "Bradford_dissolvable_agent.bin", but I can't get it to run.  I won't include the whole file, but here is the readable portion.  When I run it, I get "syntax error near unexpected token `2' ".  Sorry for the large wall of code...

```
#!/bin/sh

errorMessage() # str title , str message 
{
    title=$1
    message=$2
    if [ -x "`which zenity 2>/dev/null`" ]
    then
        zenity --title "$title" --error --text "$message"
    elif [ -x "`which kdialog 2>/dev/null`" ]
    then
        kdalog --title "$title" --error "$message"
    elif [ -x "`which xmessage 2>/dev/null`" ]
    then
        xmessage -center -buttons "OK" "$message"
    fi
    echo "$title :: $message"
}

lsb_release=/usr/bin/lsb_release

if [ -x "/bin/lsb_release" ]
then
 lsb_release=/bin/lsb_release
fi
dlg_title=`basename $0`
if [ -x "$lsb_release" ]
then
    $lsb_release -v | grep -E "core-(3|4)\..-(ia32|x86_64)" >/dev/null
    if [ $? -eq 0 ]
    then
        SKIP=`awk '/^#__BEGIN_BINARY__/ { print NR +1; exit 0; }' "$0"`
        tail -n +$SKIP "$0" >"$0.bin"
        chmod +x "$0.bin"
        if [ -x /usr/bin/xdg-mime ]
        then
            defaultHTML="`/usr/bin/xdg-mime query default text/html 2>/dev/null`"
            browser=""
            if [ -z "$XDG_DATA_HOME" ]
            then
                XDG_DATA_HOME=$HOME/.local/share
            fi

            if [ -e $XDG_DATA_HOME/applications/preferred-web-browser.desktop ]
            then
                browser="preferred-web-browser"
            elif [ -e /usr/share/applications/mozilla-firefox.desktop ]
            then
                browser="mozilla-firefox"
            elif [ -e /usr/share/applications/iceweasel.desktop ]
            then
                browser="iceweasel"
            elif [ -e /usr/share/applications/konqueror.desktop ]
            then
                browser="konqueror"
            elif [ -e /usr/share/applications/epiphany.desktop ]
            then
                browser="epiphany"
            elif [ -e /usr/local/share/applications/opera.desktop ]
            then
                browser="opera"
            elif [ -e /usr/share/applications/mozilla-seamonkey.desktop ]
            then
                browser="mozilla-seamonkey"
            fi
            
            if [ -s "$browser" ]
            then
                /usr/bin/xdg-mime default $browser.desktop text/html 2>/dev/null
            fi
        fi
        if [ -x /usr/bin/xdg-mime ]
        then
            /usr/bin/xdg-mime default $defaultHTML text/html 2>/dev/null
        fi
        thedir="`dirname "$0"`"
        thefile="`basename "$0"`"
        error_message="$("$thedir/./$thefile.bin")"
        if [ $? -eq 0 ]
        then
            rm "$0"
            rm "$0.bin"
            exit
        else
            errorMessage "$thefile" "$error_message"
        fi
    else
        errorMessage "$dlg_title" "LSB 3.0 or higher not found.  Please install the appropriate LSB packages."
    fi
else
    errorMessage "$dlg_title" "$lsb_release not found.  Please install the appropriate LSB packages."
fi

#clean up intermediary file just in case
if [ -e "$0.bin" ]
then
    rm "$0.bin"
fi

exit 
```

---

