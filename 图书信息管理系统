#include <iostream>
#include <string>
using namespace std;

// 定义图书信息结构体
struct Book {
    string ISBN; // ISBN号
    string name; // 书名
    double price; // 定价
    Book* next; // 指向下一个节点的指针
};

// 插入节点
void insert(Book* head, Book* book) {
    Book* p = head;
    while (p->next != NULL) {
        p = p->next;
    }
    p->next = book;
    book->next = NULL;
}

// 删除节点
void remove(Book* head, string ISBN) {
    Book* p = head;
    while (p->next != NULL) {
        if (p->next->ISBN == ISBN) {
            Book* q = p->next;
            p->next = q->next;
            delete q;
            return;
        }
        p = p->next;
    }
}

// 修改节点
void modify(Book* head, string ISBN, string name, double price) {
    Book* p = head->next;
    while (p != NULL) {
        if (p->ISBN == ISBN) {
            p->name = name;
            p->price = price;
            return;
        }
        p = p->next;
    }
}

// 查找节点
Book* find(Book* head, string ISBN) {
    Book* p = head->next;
    while (p != NULL) {
        if (p->ISBN == ISBN) {
            return p;
        }
        p = p->next;
    }
    return NULL;
}

// 计数节点
int count(Book* head) {
    int cnt = 0;
    Book* p = head->next;
    while (p != NULL) {
        cnt++;
        p = p->next;
    }
    return cnt;
}

// 查看所有图书信息
void viewAll(Book* head) {
    int choice;
    cout << "请选择查看哪个信息：" << endl;
    cout << "1. ISBN" << endl;
    cout << "2. 书名" << endl;
    cout << "3. 所有信息" << endl;
    cin >> choice;
    Book* p = head->next;
    int cnt = 1;
    cout << "所有图书信息如下：" << endl;
    while (p != NULL) {
        if (choice == 1) {
            cout << cnt << ". ISBN号：" << p->ISBN << endl;
        } else if (choice == 2) {
            cout << cnt << ". 书名：" << p->name << endl;
        } else {
            cout << cnt << ". ISBN号：" << p->ISBN << " 书名：" << p->name << " 定价：" << p->price << endl;
        }
        cnt++;
        p = p->next;
    }
    if (choice != 3) {
        cout << endl;
        cout << "请输入要查看的书籍的" << (choice == 1 ? "ISBN号" : "书名") << "：";
        string info;
        cin >> info;
        Book* book = find(head, info);
        if (book != NULL) {
            cout << "ISBN号：" << book->ISBN << endl;
            cout << "书名：" << book->name << endl;
            cout << "定价：" << book->price << endl;
            cout << endl;
        } else {
            cout << "未找到该书籍！" << endl;
        }
    }
}


// 主函数
int main() {
    Book* head = new Book; // 头节点
    head->next = NULL;
    int choice;
    string ISBN, name;
    double price;
    while (true) {
        cout << endl;
        cout << "图书信息管理系统" << endl;
        cout << "请选择操作：" << endl;
        cout << "1. 插入图书信息" << endl;
        cout << "2. 删除图书信息" << endl;
        cout << "3. 修改图书信息" << endl;
        cout << "4. 查找图书信息" << endl;
        cout << "5. 统计图书数量" << endl;
        cout << "6. 查看所有图书信息" << endl;
        cout << "7. 退出" << endl;
        cout << endl;
        cin >> choice;
        cout << endl; // 分隔菜单和结果
        switch (choice) {
            case 1: {
                cout << "请输入ISBN号：";
                cin >> ISBN;
                cout << "请输入书名：";
                cin >> name;
                cout << "请输入定价：";
                cin >> price;
                Book* book = new Book;
                book->ISBN = ISBN;
                book->name = name;
                book->price = price;
                insert(head, book);
                cout << "插入成功！" << endl;
                break;
            }
            case 2: {
                cout << "请输入要删除的图书的ISBN号：";
                cin >> ISBN;
                remove(head, ISBN);
                cout << "删除成功！" << endl;
                cout << endl;
                break;
            }
            case 3: {
                cout << "请输入要修改的图书的ISBN号：";
                cin >> ISBN;
                cout << "请输入新的书名：";
                cin >> name;
                cout << "请输入新的定价：";
                cin >> price;
                modify(head, ISBN, name, price);
                cout << "修改成功！" << endl;
                cout << endl;
                break;
            }
            case 4: {
                cout << "请输入要查找的图书的ISBN号或书名：";
                cin >> ISBN;
                Book* book = find(head, ISBN);
                if (book != NULL) {
                    cout << "ISBN号：" << book->ISBN << endl;
                    cout << "书名：" << book->name << endl;
                    cout << "定价：" << book->price << endl;
                } else {
                    cout << "未找到该书籍！" << endl;
                }
                break;
            }
            case 5: {
                int cnt = count(head);
                cout << "图书数量为：" << cnt << endl;
                break;
            }
            case 6: {
                viewAll(head);
                break;
            }
            case 7: {
                return 0;
            }
            default: {
                cout << "输入有误，请重新输入！" << endl;
                break;
            }
        }
    }
}
