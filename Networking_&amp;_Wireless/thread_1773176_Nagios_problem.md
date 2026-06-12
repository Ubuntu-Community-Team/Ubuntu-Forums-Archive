---
title: "Nagios problem"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Tres_Iqus on 2011-06-01
I have a problem with monitoring to MS Windows machines, with some specific services

nt.cfg
```

# 'check_nt' command definition
define command {
    command_name    check_nt
    command_line    /usr/lib/nagios/plugins/check_nt -H '$HOSTADDRESS$' -s 123asd -p 12489 -v '$ARG1$' '$ARG2$'
}

# 'check_nscp' command definition
define command {
    command_name    check_nscp
    command_line    /usr/lib/nagios/plugins/check_nt -H '$HOSTADDRESS$' -s 123asd -p 12489 -v '$ARG1$'

```

windows.cfg
```

define service{
    use            generic-service
    host_name        winserver
    service_description    NSClient++ Version
    check_command        check_nscp!CLIENTVERSION
    }

# Create a service for monitoring the uptime of the server
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    Uptime
    check_command        check_nscp!UPTIME
    }


# Create a service for monitoring CPU load
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    CPU Load
    check_command        check_nt!CPULOAD!-1 5,80,90
   }

# Create a service for monitoring memory usage
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    Memory Usage
    check_command        check_nscp!MEMUSE!-w 80 -c 90
    }

# Create a service for monitoring C:\ disk usage
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    C:\ Drive Space
    check_command        check_nt!USEDDISKSPACE!-l c -w 80 -c 90
    }

```
[B]
Service USEDDISKSPACE, CPULOAD not work =([/B]

---

