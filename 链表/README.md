# https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteNode(ListNode* head, int val) {
        ListNode *p = head;
        ListNode *q = nullptr;
        if(p->val == val)
        {
            return p->next;
        }
        while(p!=nullptr)
        {
            if(p->val == val)
            {
                q->next = p->next;
                return head;
            }
            q = p;
            p = p->next;
        }
        return head;
    }
};
```

# https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/submissions/

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if(n == 1&&head->next == nullptr)
        {
            return nullptr;
        }
        ListNode* m = head;
        ListNode* p = head;
        ListNode *q = nullptr;
        while(n--)
        {
            q = m->next;
            m = m->next;
        }
        if(q == nullptr)
        {
            return head->next;
        }
        while(q!=nullptr)
        {
            q = q->next;
            m = p;
            p = p->next;
        }
        m->next = p->next;
        return head;


    }
};
```

## 加入头结点 temp->next = head
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode *temp = new ListNode(-1);
        temp->next = head;
        ListNode *pre = temp;
        ListNode *fast = head;
        while(n--)
        {
            fast = fast->next;
        }
        while(fast!=nullptr)
        {
            fast = fast->next;
            pre = pre->next;
        }
        pre->next = pre->next->next;
        return temp->next;
    }
};
```

# https://leetcode-cn.com/problems/rotate-list/comments/

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if(!head)
        {
            return nullptr;
        }
        // if(head->next = nullptr)
        // {
        //     return head;
        // }
        ListNode *temp = new ListNode(-1);
        temp->next = head;
        ListNode *len = head;
        int lens=0;
        while(len!=nullptr)
        {
            len = len->next;
            lens++;
        }
        k = k%lens;
        while(k--&&temp->next!=nullptr)
        {
            ListNode *p = temp->next;
            ListNode *q = temp->next;
            if(q->next == nullptr)
            {
                return temp->next;
            }
            while(q->next->next!=nullptr)
            {
                q = q->next;
            }
            p = q->next;
            q->next = nullptr;   
            p->next = temp->next;
            temp->next = p;
        }
        return temp->next;
    }
};
```

# https://leetcode-cn.com/problems/linked-list-cycle/submissions/
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        unordered_set<ListNode*> set;
        while(head!=nullptr){
            if(set.count(head))
            {
                return true;
            }
            set.insert(head);
            head = head->next;
        }
        return false;
    }
};
```
# https://leetcode-cn.com/problems/linked-list-cycle-ii/
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        unordered_set<ListNode*> set;
        while(head!=nullptr){
            if(set.count(head))
            {
                return head;
            }
            set.insert(head);
            head = head->next;
        }
        return nullptr;
    }
};
```

# 两数相加  https://leetcode-cn.com/problems/two-sum/submissions/

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        //vector<int> ans;
        for(int i=0;i<nums.size();i++)
        {
            for(int j=0;j<nums.size();j++)
            {
                if(j == i)
                {
                    continue;
                }
                if(nums[i] + nums[j] == target)
                {
                    
                    // ans.push_back(i);
                    // ans.push_back(j);
                    return vector<int>{i,j};
                }
            }
        }
        return vector<int> {};
    }
};
```
