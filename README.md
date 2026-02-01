# F024 RNN+Vue+Flask电影推荐可视化系统 python flask mysql 深度学习 echarts

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从git来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 
B站up账号:  **麦麦大数据**
关注B站，有好处！
编号:  F024 RNN
## 视频

[video(video-NoWQiRGu-1760419344830)(type-bilibili)(url-https://player.bilibili.com/player.html?aid=603415628)(image-https://i-blog.csdnimg.cn/img_convert/d9d7f75724f9b719c51835436debec01.jpeg)(title-RNN 深度学习电影推荐可视化系统 vue+flask python  pytorch 循环神经网络  mysql)]

## 1 系统简介
系统简介：本系统是一个基于Vue+Flask构建的电影智能推荐系统，集推荐算法（包括基于用户协同过滤UserCF、基于物品协同过滤ItemCF以及基于循环神经网络RNN的推荐模型）和多维度数据分析于一体。系统的核心功能包括：首页展示（系统导航与推荐入口）、电影信息浏览、推荐算法模块（支持多种推荐模型的切换与对比）、电影数据可视化分析（如导演-演员网络、类型热度趋势图、评分分布直方图等），以及用户管理功能。系统通过直观的可视化图表（使用Echarts构建）帮助用户了解电影趋势与热门题材动态。同时，系统结合多种推荐模型，为用户个性化推荐感兴趣的影片，提升浏览与观影体验。用户可在系统中注册、登录，管理个人资料，查看推荐列表，并对电影进行评分和反馈，提升算法精度与系统互动性。
## 2 功能设计
系统采用B/S（浏览器/服务器）架构模式，用户通过浏览器访问由Vue.js构建的前端界面。前端的核心技术栈包括：Vue.js、Vuex（状态管理）、Vue Router（路由管理）以及ECharts（数据可视化）。前端通过RESTful API与Flask后端交互，完成用户请求的处理与数据返回。Flask后端负责核心业务逻辑的处理，包括推荐算法的运行、用户行为分析、后端接口服务的提供等。后端使用SQLAlchemy连接MySQL数据库，实现用户信息、电影元数据、评分数据和推荐结果的持久化存储与查询。推荐模块中，基于RNN的推荐模型通过分析用户的浏览记录，利用时序数据提取用户行为模式，并结合用户历史行为数据进行个性化推荐。系统还支持传统的协同过滤算法，用户和物品的协同推荐结果可与RNN推荐结果进行对比分析，以提升推荐的多样性和准确性。
### 2.1系统架构图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/58dbd69237a64c2abd0a005b91ab66f6.png)
### 1. 用户前端
**用户**通过浏览器访问系统，前端采用了基于 Vue.js 的技术栈来构建。
- **浏览器**：作为用户与系统交互的媒介，用户通过浏览器进行各种操作，如浏览图书、获取推荐等。
- **Vue 前端**：使用 Vue.js 框架搭建前端界面，包含 HTML、CSS、JavaScript，以及 Vuex（用于状态管理），vue-router（用于路由管理），和 Echarts（用于数据可视化）等组件。前端向后端发送请求并接收响应，展示处理后的数据。
### 2. 后端服务
后端服务采用 Flask 框架，负责处理前端请求，执行业务逻辑，并与数据库进行交互。
- **Flask 后端**：使用 Python 编写，借助 Flask 框架处理 HTTP 请求。通过 SQLAlchemy 与 MySQL 进行交互，通过 py2neo 与 Neo4j 进行交互。后端主要负责业务逻辑处理、 数据查询、数据分析以及推荐算法的实现。
### 3. 数据库
系统使用了两种数据库：关系型数据库 MySQL 和图数据库 Neo4j。
- **MySQL**：存储从网络爬取的基本数据。数据爬取程序从外部数据源获取数据，并将其存储在 MySQL 中。MySQL 主要用于存储和管理结构化数据。
### 4. 数据爬取与处理
数据通过爬虫从外部数据源获取，并存储在 MySQL 数据库中。
- **爬虫**：实现数据采集，从网络数据源抓取相关信息。爬取的数据首先存储在 MySQL 数据库中。
## 3 功能展示
### 3.1 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d078d469b56741619b381a5124a4c644.png)
### 3.2 登录 & 注册
登录注册做的是一个可以切换的登录注册界面，点击去登录后者去注册可以切换，背景是一个视频，循环播放。
登录需要验证用户名和密码是否正确，如果**不正确会有错误提示**。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/f3f0b9b6218d45d8881aa0484600b28f.png)
注册需要**验证用户名是否存在**，如果错误会有提示。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/64a48ed65ee4456183e7bfbe40d8522c.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ec5fd52eea854f96939053e317428179.png)
### 3.3 主页
主页的布局采用了左侧是菜单，右侧是操作面板的布局方法，右侧的上方还有用户的头像和退出按钮，如果是新注册用户，没有头像，这边则不显示，需要在个人设置中上传了头像之后就会显示。
数据统计包含了系统内各种类型的电影还有各个国家电影的统计情况：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/df42471de596497a9537d656696d2aa8.png)
### 3.4 推荐算法
**算法一 UserCF**:
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8047c253f20c4ef29f3bdf7fcc00fe76.png)
**算法二 ItemCF**:
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/399d51ea912a44de87178430bfa3200b.png)
**算法三 RNN**
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b87e0c5e76cc448bae92056ff93d5a29.png)
### 3.5 数据分析
电影分析：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e2fd598e20874d8b82ff753a683a26cc.png)
评分分析：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/bf98b0bb5db34ceca3681e9d2428c494.png)
电影地图：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a96193de4e064a178b965566e83120df.png)
词云分析：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c65a396084384fed98a4a856f11ad0a3.png)
### 3.7 登录和注册
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/48a099fe585e47ed9415ddf4e02b5e29.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a75bed35908c4a1f9ff2f5e498ee82c2.png)
### 3.8 浏览历史
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d73112ff7d55415daa53a82c0f2cdeef.png)
## 4程序代码
### 4.1 代码说明
以下是一个基于RNN的电影推荐系统的Python实现代码。该系统利用用户的浏览历史数据，通过RNN模型预测用户对未见电影的偏好。代码主要包括数据预处理、模型构建、训练和推荐生成四个部分。
### 4.2 流程图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/362fbca019894b178a0499d4df562527.png)

### 4.3 代码实例
```python
import pandas as pd
import numpy as np
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Embedding, LSTM, Dense
# 数据预处理
def preprocess_data(history_data, movie_id_dict, user_id_dict):
    # 将用户ID和电影ID转换为索引
    history_data['user_id'] = history_data['user_id'].map(user_id_dict)
    history_data['movie_id'] = history_data['movie_id'].map(movie_id_dict)
    
    # 创建用户-电影评分矩阵
    num_users = len(user_id_dict)
    num_movies = len(movie_id_dict)
    rating_matrix = np.zeros((num_users, num_movies))
    
    for index, row in history_data.iterrows():
        user_idx = row['user_id']
        movie_idx = row['movie_id']
        rating_matrix[user_idx][movie_idx] = 1  # 假设1表示观看，0表示未观看
    
    return rating_matrix
# 构建RNN模型
def build_rnn_model(num_movies, num_users):
    model = Sequential()
    model.add(Embedding(input_dim=num_movies, output_dim=64, input_length=1))
    model.add(LSTM(units=64, return_sequences=True))
    model.add(Dense(1, activation='sigmoid'))
    model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
    return model
# 生成推荐
def generate_recommendations(user_id, model, movie_id_dict, rating_matrix, top_n=5):
    user_idx = user_id_dict[user_id]
    predictions = model.predict(rating_matrix[user_idx])
    predicted_movies = np.argsort(-predictions)
    
    recommendations = []
    for movie_idx in predicted_movies[:top_n]:
        if movie_id_dict[movie_idx] not in history_data['movie_id']:
            recommendations.append(movie_id_dict[movie_idx])
    
    return recommendations
# 主函数
if __name__ == '__main__':
    # 加载数据
    history_data = pd.read_csv('tb_history.csv')
    
    # 创建映射字典
    movie_id_dict = {movie: idx for idx, movie in enumerate(history_data['movie_id'].unique())}
    user_id_dict = {user: idx for idx, user in enumerate(history_data['user_id'].unique())}
    
    # 数据预处理
    rating_matrix = preprocess_data(history_data, movie_id_dict, user_id_dict)
    
    # 构建模型
    model = build_rnn_model(len(movie_id_dict), len(user_id_dict))
    
    # 训练模型
    model.fit(history_data, epochs=10, batch_size=32, validation_split=0.2)
    
    # 生成推荐
    recommendations = generate_recommendations(1, model, movie_id_dict, rating_matrix)
    print(recommendations)
```
