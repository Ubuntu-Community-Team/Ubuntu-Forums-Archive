---
title: "radius Acct-Session-Id with perl problem"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by yasam on 2009-01-06
i have a perl file to update radius and the lines like

my $statustype = $ENV{'ACCT_STATUS_TYPE'};
my $uniqueId = $ENV{'ACCT_UNIQUE_ID'};
my $username = $ENV{'USER_NAME'};

the two variables $statustype and $username ok but""" i can't get $uniqueId """"""

modules {
    realm fillrealm {
    format = prefix
    delimiter = "@"
    }
    files {
    usersfile = ${confdir}/users
    }
    exec dialerccip {
    wait = no
    program = "/usr/local/sbin/radacct.pl"
    input_pairs = request
    }
    detail {
    detailfile = ${radacctdir}/%{Client-IP-Address}/detail-%Y%m%d
    detailperm = 0600
    }
    detail auth_log {
    detailfile = ${radacctdir}/%{Client-IP-Address}/auth-detail-%Y%m%d
    detailperm = 0600
    }
    acct_unique {
    key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
    }
    $INCLUDE ${confdir}/sql.conf
}

importand part :


acct_unique {
    key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
    }
Does anyone help me about it please?

---

