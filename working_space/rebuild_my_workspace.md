# Conda
```bash
conda --version # check version:
conda update conda # update conda: , install outside env
conda create -n my_env_name python=3.6 anaconda # build environment
conda info --envs # check envs
conda env list # all envs to view
conda create --name new_env --clone existed_env # clone an env
conda remove --name old_env --all # delete an env
conda env export > environment.yml # 输出env
conda env create -f environment.yml # build env from yml
```

# 重建工作平台
```bash
# 下载安装miniconda
conda create -n experiment3.5 python=3.5
# debug
pip install pdbpp
conda install scipy numpy matplotlib bcolz pandas autograd
conda install tensorflow keras
# 如果反复遇到报错，可以试试将 conda换成pip
# 更新最新版tensorflow
pip install tensorflow-1.3.0rc2-py3-none-any.whl
# 技术指标
brew install ta-lib
pip install TA-Lib
```

# debug工具
```bash
pip install pdbpp
python -m pdb file-name.py
# 原来进入代码，输入insert import pdb; pdb.set_trace() 来debug已经不需要了
sticky # 看到全局代码
ll # 从debug跳回到全局代码
# l 20
# l 1, 20: see line from 1 to 20
s # step into a function
n # 运行下一行
w # call stack, where I started and where I am in source code, d go down a stack, u to go up a stack
b 88 # 运行到88行，暂停
# b file.py:41 or b func_name
# b 11, this_year==2017: conditional breakpoint, at line 11 to breakpoint, if this_year == 2017
cl 1 # 删除第一个breakpoint
r # 运行所在 function
c # 运行直到结束
q # 终止
? # 查看文档
hit return # 重复上一次操作
pp variable_name # 友好打印 该变量
# 完成当前loop: until
```

# 构建bash_profile
```bash
cd # go to home directory
nano .bash_profile # go inside .bash_profile:
alias wk3.5='cd ~/.Downloads; source activate experiment3.5' # add alias
ctrl + x, y, enter # save and exit:
source .bash_profile # source to activate:
wk3.5 # - then use  everywhere
```

# 构建pdbrc
```python
alias dr pp dir(%1) # 查看everything underneath the object
alias dt pp %1.__dict__ # 查看object's dictionaries
alias pdt for k, v in %1.items(): print(k, ": ", v) # 查看一个纯 python dictionary
alias loc locals().keys() # local variables
alias doc from inspect import getdoc; from pprint import pprint; pprint(getdoc(%1)) # documents
alias sources from inspect import getsourcelines; from pprint import pprint; pprint(getsourcelines(%1)) # source code
alias module from inspect import getmodule; from pprint import pprint; pprint(getmodule(%1)) # module name
alias fullargs from inspect import getfullargspec; from pprint import pprint; pprint(getfullargspec(%1)) # all arguments names
alias opt_param optimizer.param_groups[0]['params'][%1] # all parameters
alias opt_grad optimizer.param_groups[0]['params'][%1].grad # all gradients of parameters
```

# git
```bash
# make my fork from official
# copy git repo link for clone
git clone paste_link# from my fork
cd my_fork
git remote add upstream official-url-git # link to official repo
git pull upstream master # pull from official version
# git merge upstream/master # when necessary
git push # update my own fork version
git pull # pull from my own fork version

git push origin --delete a_remote_branch_name # to delete a branch remote in github
svn checkout url-folder-replace-tree/master-with-trunk # only download part of a repo

git branch # check all branches
git branch new_branch_name # create a branch from where we are
git branch -m a_new_name # rename
git branch -d branch_to_go # delete
git checkout new_branch # switch to a new branch

git merge new_branch # from where we are, merge new_branch into where we are.

git status
git add .
git commit -m "comment"
git push

git reset # to undo git add .
```
