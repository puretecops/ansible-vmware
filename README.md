#
# Ansible VMware cloning playbook
# by Andy Parsons 12/3/2019
# aparsons@purestorage.com
#
### ### ### ### ### ### ### ### ### ### ###

# Singapore Lab VMware Cloning playbook
This playbook will create a new VM from template in VCenter. It will use the clone.csv file
to configure variables about the VM. You can also use the file to remove the VM by changing variables
from "Poweredon" to "absent", and from "present" to "absent".


# Using the CSV
You can add new items in the "clone.csv" file ensure the format is as follows
hname,address,gate,vlan,status,frc,temp,infstate

- hname=hostname name of VM to be added to VCenter
- address=IP address IP address to be assigned to system (make sure its free!)
- gate=default gateway Default gateway to be used
- vlan=portgropu in vcenter
- status=powerdon/absent Power on/remove vm from vcenter
- temp=Template2clone server2019template,apcent7template,ubuntu1604,windows2016_template
- infstate=True/False Force all actions and ignore errors
- nic=True/False Start VM with nic connected or not


# Running the playbook
ansible-playbook clonevms.yaml
You will be prompted for the password of the VCenter server srv-vc02 (check the wiki)
This will create many VMs or a single VM. You can use the Clonemaster as a sample.
- clonevm.yaml creates vms based on data in the csv

# Requires the following library to run
https://github.com/mkouhei/ansible-role-includecsv
