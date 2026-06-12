---
title: "send nagios sms notification using gammu"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by nueqs on 2011-04-17
hello everyone. i'm just install nagios in my linux box. and i configure it according to nagios documentation. the email notification working as well but the sms notification is not working. this is my configuration file...

command.cfg

> # 'host-notify-by-sms' command definition
define command{
command_name      host-notify-by-sms
command_line     /usr/bin/printf "%b" "NAGIOS / Host: "$HOSTNAME$" / State: $HOSTSTATE$ / Info:$HOSTOUTPUT$ / Date:$SHORTDATETIME$" | /usr/bin/gammu --sendsms TEXT $CONTACTPAGER$
}

# 'notify-by-sms' command definition
define command{
command_name     notify-by-sms
command_line     /usr/bin/printf "%b" "NAGIOS / Host: "$HOSTALIAS$" / State: $SERVICESTATE$ / Info:$SERVICEOUTPUT$ / Date:$SHORTDATETIME$" | /usr/bin/gammu --sendsms TEXT $CONTACTPAGER$
}

contact.cfg

>     define contact{

        contact_name                           sms
        alias                                         sms
        service_notification_period         24x7
        host_notification_period              24x7
        service_notification_options        c,r
        host_notification_options            d,r
        service_notification_commands   notify-by-sms
        host_notification_commands        host-notify-by-sms
        pager                                        013XXXXXXX
 }

define contactgroup{
        contactgroup_name          admins
        alias                               Nagios Administrators
        members                         email, sms
        }



and i also can using gammu by using command

echo "testing" | gammu --sendsms TEXT 013XXXXXXX

anyone kwow how to solve this problem?i'm sorry if i post this threat at the wrong forum.... :(:confused:

---

### Post by howefield on 2011-04-17
Thread moved to "*Networking & Wireless*"

---

### Post by nueqs on 2011-04-17
somebody help me please.....

---

### Post by luddgopelle on 2011-08-22
I am currently trying a similar setup that isn't sending.
But looking at your setup I believe you cannot have pager and $CONTACTPAGER$ defined for the extra notification addresses, you shall use address*n* and the macro $CONTACTADDRESS*n*$

Edit: sorry, I see that pager is defined as a macro. Carry on...

---

