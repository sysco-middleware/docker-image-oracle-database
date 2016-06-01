# Docker Image: Oracle Database

Image with Oracle Database installed.

## Base image

syscomiddleware/oraclelinux

## Ansible roles

- sysco-middleware.oracle-database

> ansible-galaxy install -f sysco-middleware.oracle-database

## How to build it

Define installers path:

```yaml
volumes:
  - "/opt/installers/oracle/db/11.2/database/11.2.0.4:/srv/files"
```

Make sure to unzip installers in this directory and update this file:
database/stage/cvu/cvu_prereq.xml
```xml
<RUNLEVEL>
  <LIST>
    <VALUE>3</VALUE>
    <VALUE>5</VALUE>
  </LIST>
</RUNLEVEL>
```

into

```xml
<RUNLEVEL SEVERITY="IGNORABLE">
  <LIST>
    <VALUE>3</VALUE>
    <VALUE>5</VALUE>
  </LIST>
</RUNLEVEL>
```

To be able to run Oracle Database on Docker containers.

And run:

> ansible-playbook main.yml

## Tags

- 11.2.0.4-se-oraclelinux6.7

- 12.1.0.2-se-oraclelinux6.7
